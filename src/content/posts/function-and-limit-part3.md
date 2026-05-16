---
title: 考研数学笔记：函数与极限Part 03
published: 2026-05-16
description: 继续做题，继续总结
tags: [考研, 数学, 笔记]
category: 考研
draft: false
---

## 0. 四道题目详解

*今天做题目的时候，遇到了四道题目初见完全没有思路，无从下手，特此记录*

### 题目一

求
$$
\lim_{x \to 0} x \cdot \left[ \frac{2}{x} \right]
$$
其中 $[t]$ 表示不超过 $t$ 的最大整数（向下取整）。

**分析**  
取整函数有经典不等式：
$$
t - 1 < [t] \le t
$$
令 $t = \frac{2}{x}$。由于 $x \to 0$ 时 $t$ 的符号取决于 $x$ 的符号，需要分左右极限讨论。

**解**  

先考虑 $x \to 0^+$，此时 $t = \frac{2}{x} > 0$。

由不等式：
$$
\frac{2}{x} - 1 < \left[ \frac{2}{x} \right] \le \frac{2}{x}
$$
乘以正数 $x > 0$（不等号方向不变）：
$$
2 - x < x\left[ \frac{2}{x} \right] \le 2
$$
当 $x \to 0^+$ 时，左边 $2 - x \to 2$，右边恒为 $2$，由夹逼准则：
$$
\lim_{x \to 0^+} x\left[ \frac{2}{x} \right] = 2
$$

再考虑 $x \to 0^-$，令 $x = -u$，其中 $u \to 0^+$，则：
$$
x\left[ \frac{2}{x} \right] = (-u) \left[ -\frac{2}{u} \right]
$$
负数的取整有一个重要等式（当 $y$ 不是整数时成立，而 $\frac{2}{u}$ 在 $u \to 0^+$ 时几乎总不是整数）：
$$
[-y] = -[y] - 1
$$
代入 $y = \frac{2}{u}$：
$$
\left[ -\frac{2}{u} \right] = -\left[ \frac{2}{u} \right] - 1
$$
于是：
$$
x\left[ \frac{2}{x} \right] = (-u) \left( -\left[ \frac{2}{u} \right] - 1 \right) = u\left[ \frac{2}{u} \right] + u
$$
当 $u \to 0^+$ 时，由右极限的结果，$u\left[ \frac{2}{u} \right] \to 2$，且 $u \to 0$，所以：
$$
\lim_{x \to 0^-} x\left[ \frac{2}{x} \right] = 2 + 0 = 2
$$

左右极限相等，因此：
$$
\boxed{2}
$$

---

### 题目二

求
$$
\lim_{x \to 0} \left[ \frac{x^2 \sin\frac{1}{x^2}}{\sin x} + \left( \frac{3 - e^x}{2 + x} \right)^{1/x} \right]
$$

**分析**  
这个极限是两项相加，可以分别处理。第一项分子有振荡因子 $\sin(1/x^2)$，但乘以 $x^2$ 后会趋于 0；第二项是典型的 $1^\infty$ 型未定式，用取对数法。

**解**  

**第一部分**：
$$
\left| \frac{x^2 \sin\frac{1}{x^2}}{\sin x} \right| \le \frac{x^2}{|\sin x|}
$$
当 $x \to 0$ 时，$\sin x \sim x$，所以：
$$
\frac{x^2}{|\sin x|} \sim \frac{x^2}{|x|} = |x| \to 0
$$
由夹逼准则，第一部分 $\to 0$。

**第二部分**：
令 $A(x) = \frac{3 - e^x}{2 + x}$，先求 $A(x)$ 在 $x=0$ 附近的展开。
$$
e^x = 1 + x + \frac{x^2}{2} + o(x^2)
$$
$$
3 - e^x = 2 - x - \frac{x^2}{2} + o(x^2)
$$
$$
\frac{1}{2 + x} = \frac12 \cdot \frac{1}{1 + x/2} = \frac12 \left( 1 - \frac{x}{2} + \frac{x^2}{4} + o(x^2) \right)
$$
相乘：
$$
A(x) = \left( 2 - x - \frac{x^2}{2} \right) \cdot \frac12 \left( 1 - \frac{x}{2} + \frac{x^2}{4} \right) + o(x^2)
$$
先算常数项：$2 \cdot \frac12 = 1$。  
一次项：来自 $2 \cdot \frac12 \cdot (-\frac{x}{2}) + (-x) \cdot \frac12 = -\frac{x}{2} - \frac{x}{2} = -x$。  
二次项在后续取对数时会进入更高阶，暂时不需要精确值。于是：
$$
A(x) = 1 - x + o(x)
$$

取自然对数：
$$
\ln A(x) = \ln(1 - x + o(x)) = -x + o(x)
$$
因此：
$$
\frac{1}{x} \ln A(x) = \frac{-x + o(x)}{x} = -1 + o(1) \to -1
$$
所以：
$$
\lim_{x \to 0} A(x)^{1/x} = e^{-1}
$$

**合并两部分**：第一部分 $\to 0$，第二部分 $\to e^{-1}$，因此：
$$
\boxed{\frac{1}{e}}
$$

---

### 题目三

求
$$
\lim_{x \to 0} \frac{(1 - \cos x)(x - \ln(1 + \tan x))}{(x - \sin x) \ln(1 + x)}
$$

**解**

根据等价无穷小代换，有：
$$
1 - \cos x = \frac{x^2}{2}
$$
根据泰勒级数展开：
$$
x - \sin x = \frac{x^3}{6} + o(x^3)
$$

代入原式：
$$
\text{原式} = \lim_{x \to 0} \frac{3 \big( x - \ln(1 + \tan x) \big)}{x^2}
$$

因此原极限等价于求：
$$
3 \lim_{x \to 0} \frac{x - \ln(1 + \tan x)}{x^2}
$$

现在展开 $\ln(1 + \tan x)$ 到 $x^2$ 项即可：
$$
\ln(1 + u) = u - \frac{u^2}{2} + o(u^2)
$$
代入 $u = \tan x$：
$$
x - \ln(1 + \tan x) = x - \tan x + \frac{1}{2} \tan^2 x + o(x^2)
$$
最后根据等价无穷小 $\tan x \sim x$（$x \to 0$），有：
$$
\tan x = x + o(x), \quad \tan^2 x = x^2 + o(x^2)
$$
代入得：
$$
x - \ln(1 + \tan x) = x - \big( x + o(x) \big) + \frac{1}{2} \big( x^2 + o(x^2) \big) + o(x^2) = \frac{x^2}{2} + o(x^2)
$$

代入得：
$$
3 \lim_{x \to 0} \frac{\frac{x^2}{2} + o(x^2)}{x^2} = 3 \cdot \frac{1}{2} = \frac{3}{2}
$$

$$
\boxed{\frac{3}{2}}
$$

---

### 题目四

设 $0 < x_1 < 3$，$x_{n+1} = \sqrt{x_n(3 - x_n)}$，证明 $\{x_n\}$ 极限存在并求之。

**解**

由 $x_{n+1}^2 = x_n(3 - x_n) \le \left( \frac{x_n + (3 - x_n)}{2} \right)^2 = \left( \frac{3}{2} \right)^2$，得 $0 < x_{n+1} \le \frac{3}{2}$，数列有界。

由 $x_{n+1}^2 - x_n^2 = x_n(3 - 2x_n)$ 知，当 $0 < x_n < \frac{3}{2}$ 时 $x_{n+1} > x_n$。若 $x_1 \le \frac{3}{2}$，则数列单调递增有上界 $\frac{3}{2}$；若 $x_1 > \frac{3}{2}$，则 $x_2 < \frac{3}{2}$，从第二项起单调递增趋于 $\frac{3}{2}$。故收敛。

设 $\lim x_n = L$，则 $L = \sqrt{L(3-L)}$，平方得 $2L^2 - 3L = 0$，解得 $L = 0$ 或 $L = \frac{3}{2}$，由 $x_n > 0$ 及单调性知 $L = \frac{3}{2}$。

$$
\boxed{\frac{3}{2}}
$$

---

## 1. 取整函数的极限

取整函数 $[t]$ 在 $t>0$ 时没问题，但 $t<0$ 时很多人会搞错。例如 $[-1.3] = -2$，不是 $-1$。一般地，对正数 $y$ 有：
$$
[-y] = -[y] - 1 \quad (\text{当 } y \notin \mathbb{Z})
$$
这是因为向下取整往更小的方向取，比 $-y$ 小的最大整数恰好比 $-[y]$ 还要小 $1$。

**配套练习**：

求 $\lim_{x \to 0} x \left[ \frac{1}{x} \right]$。

> 提示：分 $x \to 0^+$ 和 $x \to 0^-$，用同样的夹逼法。答案应该是 $1$（左右相等）。

---

## 2. 有界量与无穷小的乘积

遇到形如 $x^k \cdot \sin\frac{1}{x^m}$ 或 $x^k \cdot \cos\frac{1}{x^m}$ 的项，关键是：
- 正弦、余弦的绝对值 $\le 1$，所以整个乘积的绝对值 $\le |x^k|$。
- 只要 $k > 0$，当 $x \to 0$ 时 $|x^k| \to 0$，因此乘积 $\to 0$。

**注意**：如果分母也有 $x$ 的幂次，需要比较阶数。例如：
$$
\frac{x^2 \sin\frac{1}{x^2}}{\sin x} \sim \frac{x^2 \cdot O(1)}{x} = O(x) \to 0
$$
但如果分子是 $x \sin\frac{1}{x}$，分母是 $\sqrt{x}$，则 $\frac{x \sin\frac{1}{x}}{\sqrt{x}} = \sqrt{x} \sin\frac{1}{x} \to 0$ 仍然成立。关键在于分子的幂次高于分母时，整体趋于 0。

**配套练习**：

判断 $\lim_{x \to 0} \frac{x \sin\frac{1}{x}}{\sqrt{x}}$ 是否存在，若存在求值。

> 答案：$0$。因为 $\left| \frac{x \sin\frac{1}{x}}{\sqrt{x}} \right| = \sqrt{x} \cdot |\sin\frac{1}{x}| \le \sqrt{x} \to 0$。

---

## 3. $1^\infty$ 型极限的处理流程

这类极限的标准做法是：

1. 将底数写成 $1 + \alpha(x)$，其中 $\alpha(x) \to 0$。
2. 计算 $\lim \alpha(x) \cdot \text{指数}$，这通常需要泰勒展开。
3. 原极限 $= \exp\left( \lim \alpha(x) \cdot \text{指数} \right)$。

**常见错误**：直接对底数和指数分别取极限，得到 $1^\infty$ 后以为就是 $1$。这是完全错误的，因为 $1^\infty$ 是不定式。

**配套练习**：

求 $\lim_{x \to 0} \left( \frac{\sin x}{x} \right)^{1/x^2}$。

> 提示：先取对数，$\ln\left(\frac{\sin x}{x}\right) = \ln\left(1 - \frac{x^2}{6} + o(x^2)\right) \sim -\frac{x^2}{6}$，再乘以 $1/x^2$ 得 $-1/6$，所以极限是 $e^{-1/6}$。

---

## 4. 复杂分式的泰勒展开：如何确定展开阶数

这是今天最让我头疼的地方。经验是：

- **先看分母的最低阶数**。将分母各因子展开，相乘得到最低次幂。
- **分子需要展开到不低于分母的阶数**。但有时低阶项会相互抵消，所以实际需要展开到第一个非零项出现为止。
- **展开时先展开每一个因子，再乘开**，合并同类项时小心不要漏掉交叉项。

一个容易出错的地方是复合函数展开，比如 $\ln(1 + \tan x)$。不能直接把 $\tan x \sim x$ 代入对数，因为这样会丢失高阶项。正确做法是把 $\tan x$ 展开到需要的阶数，再代入 $\ln(1+u)$ 的展开式 $u - u^2/2 + u^3/3 - \cdots$，并保留到对应阶数。

**配套练习**：

求 $\lim_{x \to 0} \frac{e^x - \cos x - x}{x^3}$。

> **提示**：展开 $e^x = 1 + x + \dfrac{x^2}{2} + \dfrac{x^3}{6} + o(x^3)$，
> $\cos x = 1 - \dfrac{x^2}{2} + o(x^3)$，
> 相减得：
> $$
> e^x - \cos x - x = \left(1 + x + \frac{x^2}{2} + \frac{x^3}{6}\right) - \left(1 - \frac{x^2}{2}\right) - x + o(x^3) = x^2 + \frac{x^3}{6} + o(x^3)
> $$
> 最低阶是 $x^2$，低于分母的 $x^3$。除以 $x^3$ 得 $\dfrac{1}{x} + \dfrac{1}{6} + o(1)$，极限不存在（趋于无穷）。

这个例子说明：
- 分子最低阶 **低于** 分母最低阶 → 极限为 $\infty$（或不存在）
- 分子最低阶 **等于** 分母最低阶 → 极限为有限非零值
- 分子最低阶 **高于** 分母最低阶 → 极限为 $0$

---

## 5. 递推数列的极限：不动点 + 单调性分析

对于形如 $x_{n+1} = f(x_n)$ 的递推，若 $f$ 连续且数列收敛，则极限必为不动点方程 $x = f(x)$ 的解。但**判断收敛性**往往更难，常用方法：

- **单调有界**：证明数列单调且有界。单调性可以通过比较 $x_{n+1}$ 与 $x_n$ 的大小得到，有时需要分区间讨论。
- **压缩映射**：如果 $|f'(x)| \le k < 1$ 在某个区间内成立，则迭代收敛。

本题中，$f(x) = \sqrt{x(3-x)}$，定义域 $(0,3)$。求导得 $f'(x) = \frac{3-2x}{2\sqrt{x(3-x)}}$，在 $(0,3)$ 内不是一致压缩的，但可以通过分析平方差来判断单调性。

**配套练习**：

设 $x_1 = 1$，$x_{n+1} = \sqrt{1 + x_n}$，证明数列收敛并求极限。

> 答案：极限是方程 $L = \sqrt{1+L}$ 的正根，即 $L = \frac{1+\sqrt{5}}{2}$（黄金分割比）。单调递增有上界可用归纳法证明。

---

## 6.常用泰勒展开公式（$x \to 0$）

1. **指数函数**  
   $$
   e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots + \frac{x^n}{n!} + o(x^n)
   $$

2. **正弦函数**  
   $$
   \sin x = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \cdots + (-1)^{n-1}\frac{x^{2n-1}}{(2n-1)!} + o(x^{2n})
   $$

3. **余弦函数**  
   $$
   \cos x = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \cdots + (-1)^n\frac{x^{2n}}{(2n)!} + o(x^{2n+1})
   $$

4. **对数函数**  
   $$
   \ln(1+x) = x - \frac{x^2}{2} + \frac{x^3}{3} - \cdots + (-1)^{n-1}\frac{x^n}{n} + o(x^n)
   $$

5. **幂函数（二项式展开）**  
   $$
   (1+x)^\alpha = 1 + \alpha x + \frac{\alpha(\alpha-1)}{2!}x^2 + \cdots + \frac{\alpha(\alpha-1)\cdots(\alpha-n+1)}{n!}x^n + o(x^n)
   $$

6. **反正切函数**  
   $$
   \arctan x = x - \frac{x^3}{3} + \frac{x^5}{5} - \cdots + (-1)^{n-1}\frac{x^{2n-1}}{2n-1} + o(x^{2n})
   $$

7. **正切函数**  
   $$
   \tan x = x + \frac{x^3}{3} + \frac{2}{15}x^5 + \cdots + o(x^{2n+1})
   $$

8. **反正弦函数**  
   $$
   \arcsin x = x + \frac{x^3}{6} + \frac{3}{40}x^5 + \cdots + o(x^{2n+1})
   $$

9. **几何级数（$|x|<1$）**  
   $$
   \frac{1}{1-x} = 1 + x + x^2 + \cdots + x^n + o(x^n)
   $$

10. **几何级数变体（$|x|<1$）**  
    $$
    \frac{1}{1+x} = 1 - x + x^2 - \cdots + (-1)^n x^n + o(x^n)
    $$

---

### 高频（展开到 $x^3$ 阶）

$$
\begin{aligned}
e^x &= 1 + x + \frac{x^2}{2} + \frac{x^3}{6} + o(x^3) \\[4pt]
\sin x &= x - \frac{x^3}{6} + o(x^3) \\[4pt]
\cos x &= 1 - \frac{x^2}{2} + o(x^2) \\[4pt]
\ln(1+x) &= x - \frac{x^2}{2} + \frac{x^3}{3} + o(x^3) \\[4pt]
\tan x &= x + \frac{x^3}{3} + o(x^3) \\[4pt]
(1+x)^\alpha &= 1 + \alpha x + \frac{\alpha(\alpha-1)}{2}x^2 + \frac{\alpha(\alpha-1)(\alpha-2)}{6}x^3 + o(x^3) \\[4pt]
\arctan x &= x - \frac{x^3}{3} + o(x^3) \\[4pt]
\frac{1}{1+x} &= 1 - x + x^2 - x^3 + o(x^3)
\end{aligned}
$$

---

*这里的笔记是我复习过程中的个人记录，难免有理解不到位或计算错误的地方，欢迎指正，一起进步。*