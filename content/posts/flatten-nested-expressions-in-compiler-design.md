---
title: "树状表达式生成为扁平指令流的模式"
date: 2026-01-25
draft: false
---

最近在使 Kotlin 语言写一个 C 编译器，跟着[《Writing a C Compiler》](https://nostarch.com/writing-c-compiler)这本书。走到代码生成这一步，发现一个很自然的写法，记录一下。

## 问题

表达式是嵌套的，比如 `return -(~(-5))`。

AST 长这样：

```
Return
└── Negate
        └── Complement
            └── Negate
                    └── Constant(5)
```

但最后生成的中间代码是扁平的：

```
tmp.0 = neg 5
tmp.1 = not tmp.0
tmp.2 = neg tmp.1
return tmp.2
```

问题是怎么把树拍平？

## 模式

核心思路：每次递归调用做**两件事**：

1. **Emit** — 维护一个指令列表，往指令列表里加指令（副作用）
2. **Return** — 返回结果存在哪儿（给上层用）

代码大概长这样：

```kotlin
fun visit(expr: Expression): TackyVal {
    return when (expr) {
        is Constant -> {
            // 常量直接返回，不需要生成指令
            TackyConstantVal(expr.value)
        }
        is UnaryExpr -> {
            // 1. 先递归，拿到内层表达式的结果
            val src = visit(expr.inner)

            // 2. 生成一条指令
            val dst = TackyVariableVal(makeTemp())
            instructions.add(UnaryInst(expr.op, src, dst))

            // 3. 返回我们的结果位置，给上层用
            return dst
        }
    }
}

```

重点是：递归调用既有副作用，又有返回值。副作用是往列表里加指令，返回值是告诉调用者"我的结果存在这个临时变量里"。

走一遍

拿 `return -(~(-5))` 举例：

| 调用 | Emit | Return |
|-|-|-|
| visit 最外层 Negate | — | 先递归 |
| visit Complement | — | 先递归 |
| visit 内层 Negate | — | 先递归 |
| visit Constant(5) | 啥也没加 | Constant(5) |
| 回到内层 Negate | tmp.0 = neg 5 | tmp.0 |
| 回到 Complement | tmp.1 = not tmp.0 | tmp.1 |
| 回到最外层 Negate | tmp.2 = neg tmp.1 | tmp


递归结束，指令列表里就是拍平的代码了。

## 本质

这其实就是递归遍历 AST，只不过遍历的同时在攒指令列表。

和解析器的递归下降有点像——都是递归、每种节点一个分支——但方向相反：

- 解析器：token 流 → AST
- 代码生成：AST → 指令流

写编译器之前觉得代码生成很神秘，写完发现其实就是递归遍历树，顺便攒一个列表。没啥魔法。