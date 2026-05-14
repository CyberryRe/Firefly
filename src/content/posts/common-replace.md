---
title: 数学计算中常用的等效代换
published: 2026-05-14
description: 简单介绍等效代换
tags: [考研, 数学, 计算]
category: 考研
draft: false
---

等效代换（也称等价无穷小代换）是高等数学计算过程中的一种常见技巧，运用的频率很高，这也要求我们需要熟练的掌握这个能力。

## 等价无穷小的来源

在介绍等价无穷小之前，我们先回顾一个重要极限：

$$
\lim_{x \to 0} \frac{\sin x}{x} = 1
$$

这个极限告诉我们：当 $x \to 0$ 时，$\sin x$ 和 $x$ 的比值趋近于 1。用数学语言说，就是 **$\sin x$ 与 $x$ 是等价无穷小**，记作 $\sin x \sim x$。

类似地，我们可以推导出其他等价关系。下面就是考研数学中最常用的等价无穷小代换公式。

## 常用等价无穷小（当 $x \to 0$ 时）

以下是考研数学中最常用的等价代换公式，**建议熟记**：

### 三角函数类

1. $\sin x \sim x$
2. $\tan x \sim x$
3. $\arcsin x \sim x$
4. $\arctan x \sim x$

### 反三角函数类

5. $1 - \cos x \sim \frac{1}{2}x^2$

### 对数指数类

6. $\ln(1 + x) \sim x$
7. $e^x - 1 \sim x$
8. $a^x - 1 \sim x \ln a$（其中 $a > 0$ 且 $a \neq 1$）

### 幂函数类

9. $(1 + x)^\alpha - 1 \sim \alpha x$（其中 $\alpha$ 为常数）

特别地，当 $\alpha = \frac{1}{2}$ 时：
$$
\sqrt{1 + x} - 1 \sim \frac{1}{2}x
$$

## 使用注意事项

### ⚠️ 常见错误

**正确用法：** 等价代换只能用于**乘除因子**，不能用于**加减项**。

**错误示例：**
$$
\lim_{x \to 0} \frac{\sin x - \tan x}{x^3} \neq \lim_{x \to 0} \frac{x - x}{x^3}
$$

**正确做法：** 加减项需要提取公因式或使用泰勒展开。

### ✅ 正确示例

$$
\lim_{x \to 0} \frac{\sin 2x}{x} = \lim_{x \to 0} \frac{2x}{x} = 2
$$

$$
\lim_{x \to 0} \frac{\ln(1 + 3x)}{x} = \lim_{x \to 0} \frac{3x}{x} = 3
$$

## 进阶：泰勒展开（等价代换的本质）

等价代换实际上是泰勒展开的一阶近似。更精确的展开如下：

$$
\sin x = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \cdots
$$

$$
\cos x = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \cdots
$$

$$
e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots
$$

$$
\ln(1 + x) = x - \frac{x^2}{2} + \frac{x^3}{3} - \cdots
$$

## 实战练习题

试着用等价代换计算以下极限（答案在文末）：

1. 
$$
\lim_{x \to 0} \frac{\tan 2x}{\sin 3x}
$$

2. 
$$
\lim_{x \to 0} \frac{1 - \cos x}{x^2}
$$

3. 
$$
\lim_{x \to 0} \frac{e^{2x} - 1}{\ln(1 + 5x)}
$$

---

<details>
<summary>点击查看答案</summary>

1. $\frac{2}{3}$

2. $\frac{1}{2}$

3. $\frac{2}{5}$

</details>

---
