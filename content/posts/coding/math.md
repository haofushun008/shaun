---
title: 'Markdown数学公式'
date: 2020-03-29
tags: [md语法]
toc: true
---

 因为要使用markdown编辑数学公式然后在文档、网页中使用，但是自己总是记不住这么多东西，特别是几天不用，很多都忘记了，因此准备就数学公式的Latex编辑方式做一个整理，以方便自己和读者今后使用。

<!--more-->

#### 1.0  特殊字符

|   特殊字符   |                  说 明                  |            实例             |          完整字符串          |
| :----------: | :-------------------------------------: | :-------------------------: | :--------------------------: |
|      $       |      数学公式前后加**$**是行内公式      |      数学公式:$a=x+y$       |      数学公式:\$a=x+y$       |
|      $$      |     数学公式加$$就是读占一行的公式      |     独占一行:$$a=x+y$$      |     独占一行:\$$a=x+y$$      |
|      \       | 转义字符,特殊字符要显示原意,就在前面加\ |              $              |           \$ \ $$            |
|     \\\      |                  换行                   |        $a=x+y\\b=y$         |        \$a=x+y\\b=y$         |
|      ^       |             后跟内容为上标              |            $a^i$            |            \$a^i$            |
| \left \right |     用于自适应匹配分隔符如{,(,\|等      | $\left \frac{du}{dx} \right​ | \$\left \frac{du}{dx} \right |
|   \limits    |           强制上下限在上下侧            |  $\sum\limits_{k=1}^nkx $   |  \$\sum\limits_{k=1}^nkx $   |
|     \sum     |                  求和                   |      $\sum_{k=1}^nkx $      |      \$\sum_{k=1}^nkx $      |
|     \int     |                  积分                   |         $\int_a^b$          |         \$\int_a^b$          |

|  特殊字符   |      说 明       | 实例                             | 完整字符串                        |
| :---------: | :--------------: | -------------------------------- | --------------------------------- |
|  \nolimits  | 强制上下限在右侧 | $\sum\nolimits_{k=1}^nkx$        | \$\sum\nolimits_{k=1}^nkx$        |
|  \overline  |      上划线      | $\overline{a+b}$                 | \$\overline{a+b}$                 |
| \underline  |      下划线      | $\underline{a+b}$                | \$\underline{a+b}$                |
| \overbrace  |     上花括号     | $\overbrace{a+b+\dots+n}^{m个}$  | \$\overbrace{a+b+\dots+n}^{m个}$  |
| \underbrace |     下花括号     | $\underbrace{a+b+\dots+n}_{m个}$ | \$\underbrace{a+b+\dots+n}_{m个}$ |



#### **1.1  分数**

|          算式          |      markdown       |
| :--------------------: | :-----------------: |
| $$\frac{7x+5}{1+y^2}$$ | \frac{7x+5}{1+y^2}\ |

#### **1.2  下标**

|   算式    | markdown |
| :-------: | :------: |
| $$z=z_l$$ |  z=z_l   |

#### **1.3  省略号**

| 算式 | markdown |
| :--: | :------: |
|  ⋯⋯  |  \cdots  |

#### **1.4  行间公式**

|                             算式                             |                           markdown                           |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| $\frac{d}{dx}e^{ax}=ae^{ax}\quad\sum_{i=1}^{n}{(X_i - \overline{X})^2}$ | \frac{d}{dx}e^{ax}=ae^{ax}\quad\sum_{i=1}^{n}{(X_i - \overline{X})^2} |

#### **1.5  开根号**

|          算式          |       markdown       |
| :--------------------: | :------------------: |
| $\sqrt{2};\sqrt[n]{3}$ | \sqrt{2};\sqrt[n]{3} |

#### **1.6  矢量**

|           算式            |        markdown         |
| :-----------------------: | :---------------------: |
| $\vec{a} \cdot \vec{b}=0$ | \vec{a} \cdot \vec{b}=0 |

#### **1.7  积分**

|           算式           |        markdown        |
| :----------------------: | :--------------------: |
| $\int ^2_3 x^2 {\rm d}x$ | \int ^2_3 x^2 {\rm d}x |

#### **1.8  极限**

|              算式              |           markdown           |
| :----------------------------: | :--------------------------: |
| $\lim_{n\rightarrow+\infty} n$ | \lim_{n\rightarrow+\infty} n |

#### **1.9  累加**

|         算式         |      markdown      |
| :------------------: | :----------------: |
| $\sum \frac{1}{i^2}$ | \sum \frac{1}{i^2} |

#### **1.10  累乘**

|         算式          |      markdown       |
| :-------------------: | :-----------------: |
| $\prod \frac{1}{i^2}$ | \prod \frac{1}{i^2} |

#### **1.11  希腊字母**

|   大写    | markdown |     小写      |  markdown   |
| :-------: | :------: | :-----------: | :---------: |
|    $A$    |    A     |   $\alpha$    |   \alpha    |
|    $B$    |    B     |    $\beta$    |    \beta    |
| $\Gamma$  |  \Gamma  |   $\gamma$    |   \gamma    |
| $\Delta$  |  \Delta  |   $\delta$    |   \delta    |
|    $E$    |    E     |  $\epsilon$   |  \epsilon   |
|           |          | $\varepsilon$ | \varepsilon |
|    $Z$    |    Z     |    $\zeta$    |    \zeta    |
|    $H$    |    H     |    $\eta$     |    \eta     |
| $\Theta$  |  \Theta  |   $\theta$    |   \theta    |
|    $I$    |    I     |    $\iota$    |    \iota    |
|    $K$    |    K     |   $\kappa$    |   \kappa    |
| $\Lambda$ | \Lambda  |   $\lambda$   |   \lambda   |
|    $M$    |    M     |     $\mu$     |     \mu     |
|    $N$    |    N     |     $\nu$     |     \nu     |
|   $\Xi$   |   \Xi    |     $\xi$     |     \xi     |
|    $O$    |    O     |  $\omicron$   |  \omicron   |
|   $\Pi$   |   \Pi    |     $\pi$     |     \pi     |
|    $P$    |    P     |    $\rho$     |    \rho     |
| $\Sigma$  |  \Sigma  |   $\sigma$    |   \sigma    |
|    $T$    |    T     |    $\tau$     |    \tau     |
|    $Υ$    | \Upsilon |  $\upsilon$   |  \upsilon   |
|  $\Phi$   |   \Phi   |    $\phi$     |    \phi     |
|           |          |   $\varphi$   |   \varphi   |
|    $X$    |    X     |    $\chi$     |    \chi     |
|  $\Psi$   |   \Psi   |    $\psi$     |    \psi     |
| $\Omega$  |  \Omega  |   $\omega$    |   \omega    |

#### **1.12 三角函数**

|  算式  | markdown |
| :----: | :------: |
| $\sin$ |   \sin   |
| $\cos$ |   \cos   |
| $\tan$ |   \tan   |

#### **1.13 对数函数**

|    算式     | markdown  |
| :---------: | :-------: |
|   $\ln15$   |   \ln15   |
| $\log_2 10$ | \log_2 10 |
|   $\lg7$    |   \lg7    |

#### **1.14 关系运算符**

|  运算符  | markdown |
| :------: | :------: |
|  $\pm$   |   \pm    |
| $\times$ |  \times  |
|  $\div$  |   \div   |
|  $\sum$  |   \sum   |
| $\prod$  |  \prod   |
|  $\neq$  |   \neq   |
|  $\leq$  |   \leq   |
|  $\geq$  |   \geq   |

#### 1.15 矩阵显示

$\left|\begin{array}{lcr}a&b&c\\d&e&f\end{array}\right|$

```html
$\left|							---左边的竖线
\begin{array}				---一个array开始
{lcr}								---l/c/r表示列的对齐方式左/中/右
a&b&c\\d&e&f				---&分隔列，\\换行
\end{array}					---一个array结束
\right|$						---右边的竖线
```

