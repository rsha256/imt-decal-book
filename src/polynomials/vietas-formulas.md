<title>Vieta's Formulas – IMT DeCal</title>

# Vieta's Formulas

_by Suraj Rampure_<br>
_Last modified: March 21, 2019_

---


<br>

<!--

Jump to:
- [Naive Approach, using the Quadratic Formula](#naive)
- [Derivations](#derivations)
	- [Derivation for Polynomials of Degree 2](#degree2)
	- [Derivation for Polynomials of Degrees 3, 4](#degree34)
	- [General Vieta's, Similarity to Binomial Theorem](#general)
- [Symmetric Sums](#symmetric)
- [Example Problems](#examples)

-->

Vieta's formulas give us a way to interpret a polynomial in standard form, e.g. $$p(x) = 4x^2 + 3x + 3$$, in terms of its roots, without having to find the roots specifically. While there are more practical applications to this, the derivation of Vieta's formulas prove to be an interesting combinatoral problem.

<br>

<a name="naive">

## Naive Approach, using the Quadratic Formula
---

</a>

Let $$p(x) = ax^2 + bx + c$$. We know that $$p(x)$$ will have two roots, i.e. solutions to $$p(x) = 0$$ (they might be complex and/or equal). 

Suppose $$p(x)$$'s roots are $$r_1$$ and $$r_2$$, and suppose we want to find the sum ($$r_1 + r_2$$) and product ($$r_1 r_2$$) of these roots. One way to do this would be to use the quadratic formula to solve for both roots, and simplify.

Using the quadratic formula:

<div align=center>

$$r_1, r_2 = \frac{-b + \sqrt{b^2 - 4ac}}{2a}, \frac{-b - \sqrt{b^2 - 4ac}}{2a}$$

</div>

Then:

<div align=center>

$$r_1 + r_2 = \frac{-b + \sqrt{b^2 - 4ac} - b - \sqrt{b^2 - 4ac}}{2a} = -\frac{2b}{2a} = -\frac{b}{a}$$

$$r_1r_2 = \left( \frac{-b + \sqrt{b^2 - 4ac}}{2a} \right)\left( \frac{-b - \sqrt{b^2 - 4ac}}{2a} \right) = \frac{b^2 - (b^2 - 4ac)}{4a^2} = \frac{4ac}{4a^2} = \frac{c}{a}$$

</div>

We've found that the sum of the roots is $$-\frac{b}{a}$$, and the product of the roots is $$\frac{c}{a}$$.

How would we extend this to cubic polynomials, though? _There's a simpler way to look at this._

<br>

<a name='derivations'>

## Derivations
---

</a>


<a name = 'degree2'>

### Derivation of Vieta's Formulas for Polynomials of Degree 2
---

</a>

Again, suppose $$p(x) = ax^2 + bx + c$$ have have roots $$r_1, r_2$$. By the factor theorem (which you can read about in Chapter 5.4), we know that $$p(x) = a(x - r_1)(x - r_2)$$, for some constant $$a$$. Expanding $$p(x)$$:

<div align=center>

$$\begin{aligned}
p(x) &= a(x - r_1)(x-r_2) \\\ &= a[x^2 - (r_1 + r_2)x + r_1r_2 ] \\\ &= ax^2 - a(r_1 + r_2)x + ar_1r_2 \\\ \end{aligned}$$

</div>

Comparing this expansion with $$ax^2 + bx + c$$, we see:

<div align=center>

$$-a(r_1 + r_2) = b \implies \boxed{r_1 + r_2 = -\frac{b}{a}}$$

$$ar_1r_2 = c \implies \boxed{r_1r_2 = \frac{c}{a}}$$

</div>

These are known as **Vieta's formulas** for polynomials of degree 2. This matches the results we saw above, using the quadratic formula. However, we conducted this analysis in a way that can be extended to polynomials of any degree! 

Notice that the signs alternate:
- In $$p(x) = x^2 - 5x + 6$$, the sum of the roots is 5 and product is 6.
- In $$p(x) = x^2 + 5x + 6$$, the sum of the roots is -5 and the product is 6.

<br>

<a name='degree34'>

### Derivation of Vieta's Formulas for Polynomials of Degrees 3, 4
---

</a>

<br>

We will follow a similar process as above to derive Vieta's formulas for degree 3. However, at this point, you should try and derive these on your own, then come back here to check your work.

Assume $$p(x)$$ has roots $$r_1, r_2, r_3$$, and has the form $$p(x) = ax^3 + bx^2 + cx + d$$. Then:

<div align=center>

$$
\begin{aligned} p(x) &= a(x-r_1)(x-r_2)(x-r_3) \\\ &= a \left[(x^3 - (r_1 + r_2 + r_3)x + (r_1r_2 + r_1r_3 + r_2r_3)x - r_1r_2r_3\right] \\\ &= ax^3 - a(r_1 + r_2 + r_3)x^2 + a(r_1r_2 + r_1r_3 + r_2r_3)x - ar_1r_2r_3 \\\
\end{aligned}
$$

$$\implies \boxed{r_1 + r_2 + r_3 = -\frac{b}{a}}$$

$$\implies \boxed{r_1r_2 + r_1r_3 + r_2r_3 = \frac{c}{a}}$$

$$\implies \boxed{r_1r_2r_3 = -\frac{d}{a}}$$

</div>

<br>

Again, it should be noted that the signs alternate. The sign on the sum of the roots is always negative.

We could follow the same process to find the formulas for degrees 4, 5 and so on and so forth. However, there's a pattern here. When multiplying out $$(x - r_1)(x - r_2)(x - r_3)$$, we know our product must contain every combination of one term from the first bracket, one term from the second bracket and one term from the third bracket. Then, our choices are the following:

*   We can choose $$3$$ $$x$$s and no roots, yielding $$x^3$$

*   We can choose $$2$$ $$x$$s and one root, yielding
    $$(-r_1 - r_2 - r_3)x^2 = -(r_1+r_2+r_3)x^2$$

*   We can choose $$1$$ $$x$$ and two roots, yielding
    $$((-r_1) \cdot (-r_2) + (-r_1) \cdot (-r_3) + (-r_2) \cdot (-r_3))x = (r_1r_2 + r_1r_3 + r_2r_3)x$$

*   We can choose no $$x$$s and three roots, yielding
    $$((-r_1) \cdot (-r_2) \cdot (-r_3)) = -r_1r_2r_3$$

<br>

Each successive term is a **sum of products of roots, taken in different quantities at a time**. $$r_1 + r_2 + r_3$$ is the sum of the products of the roots, taken one at a time, since multiplying a constant by nothing is the constant itself. $$r_1r_2 + r_1r_3 + r_2r_3$$ is the sum of the product of the roots, taken two at a time – it features all 3 possible combinations of two different roots multiplied together. $$r_1r_2r_3$$ is the sum of the product of the roots, taken three at a time – there is only one way to take three items at once, and this is that one way.

Following this pattern, we can find the expansion (and Vieta's) for a degree 4 polynomial without having to do any manual expanding. Let $$p(x)$$ have roots $$r_1, r_2, r_3, r_4$$. Then, if we let $$p(x) = ax^4 + bx^3 + cx^2 + dx + e$$ we have:

<div align=center>

$$
r_1 + r_2 + r_3 + r_4 = -\frac{b}{a} \\\ r_1r_2 + r_1r_3 + r_1r_4 + r_2r_3 + r_2r_4 + r_3r_4 = \frac{c}{a} \\\ r_1r_2r_3 + r_1r_2r_4 + r_1r_3r_4 + r_2r_3r_4 = -\frac{d}{a} \\\ r_1r_2r_3r_4 = \frac{e}{a} $$

</div>


One thing to notice is that 1 term makes up the coefficient of $$x^4$$, 4 terms make up the coefficient of $$x^3$$, 6 terms make up the coefficient of $$x^2$$, 4 terms make up the coefficient of $$x$$ and 1 term makes up the coefficient of $$1$$. These numbers – 1, 4, 6, 4, 1 – are of course the 4th row of **Pascal's triangle**! This makes sense, as the coefficient of $$x^3$$ consists of the roots taken one at a time, which means there should be $${4 \choose 1} = 4$$ terms. The coefficient of $$x^2$$ consists of the roots taken two at a time, which means there should be $${4 \choose 2} = 6$$ terms.

Of course, since this is a pattern, we can generalize it to polynomials of an arbitrary degree.

<br>

<a name = 'general'>

### General Vieta's, Similarity to Binomial Theorem
---

</a>

<br>

<div align=center>

$$p(x) = \sum_{k = 0}^n a_k x^k = \sum_{k = 0}^n (-1)^{n-k} \big(\text{sum of the products of the roots of } p(x) \text{, taken } n-k \text{ at a time}  \big)x^k$$

</div>

**The binomial theorem is actually just a special case of Vieta's formulas, when all roots are the same!** For example, suppose $$n = 4$$, $$r_i = c$$ for all $$i$$ and the leading coefficient is 1. Then:

<div align=center>

$$p(x) = (x-c)^4 = {4 \choose 0}x^4 - {4 \choose 1} x^3c + {4 \choose 2}x^2c^2 - {4 \choose 3}xc^3 + {4 \choose 4}c^4$$

</div>

Using Vieta's formulas for $n = 4$:

<div align=center>

$$\begin{aligned} a_3 &= -(r_1 + r_2 + r_3 + r_4) = -4c = {4 \choose 1}(-c)^1 \\\ a_2 &= r_1r_2 + r_1r_3 + r_1r_4 + r_2r_3 + r_2r_4 + r_3r_4 = 6c^2 = {4 \choose 2}(-c)^2 \\\ a_1 &= -(r_1r_2r_3 + r_1r_2r_4 + r_1r_3r_4 + r_2r_3r_4) = -4c^3 = {4 \choose 3}(-c)^3 \\\ a_0 &= r_1r_2r_3r_4 = c^4 = {4 \choose 4}(-c)^4 \end{aligned}$$

</div>

<br>

<a name='symmetric'>

## Symmetric Sums
---

</a>

Vieta's formulas give us expressions for the sum of the roots and product of the roots of polynomials. However, we are also given expressions for sums of the form $$r_1r_2 + r_1r_3 + r_2r_3$$, for instance. 


A **symmetric sum** is an sum in which the value does not change when the order of variables are swapped. For example, $$f(a, b, c) = ab + ac + bc$$ is symmetric, because in any _permutation_ of our variables $$a, b, c$$, the value stays the same:


<div align=center>

$$\begin{aligned} f(a, b, c) &= ab + ac + bc = ab + ac + bc \\\ f(a, c, b) &= ac + ab + cb = ab + ac + bc \\\ f(b, a, c) &= ba + bc + ac = ab + ac + bc \\\ f(b, c, a) &= bc + ba + ca = ab + ac + bc \\\ f(c, a, b) &= ca + cb + ab = ab + ac + bc \\\ f(c, b, a) &= cb + ca + ba = ab + ac + bc \end{aligned}$$

</div>

More concretely, with $$n = 4$$:

<div align=center>

$$\begin{aligned} S_1 &= a + b + c + d \\\ S_2 &= ab + ac + ad + bc + bd + cd \\\ S_3 &= abc + abd + acd + bcd \\\ S_4 &= abcd \end{aligned}$$

</div>

<br>

<a name="examples">

## Example Problems
---

</a>

You should attempt each of these problems on your own before looking at the solutions that follow.

<br>

### Example 1
---

Suppose $a, b$ satisfy $x^2 - 18x + 18$. Determine $a^2 + b^2$.

<br>

**Solution:** From Vieta's, we know $$a + b = 18$$ and $$ab = 18$$. Then:

<div align=center>

$$(a+b)^2 = a^2 + b^2 + 2ab$$

$$\implies a^2 + b^2 = (a+b)^2 - 2ab = 18^2 - 2\cdot18 = \boxed{288}$$

</div>

<br>

### Example 2
---

$$p(x) = x^3 - Ax + 15$$ has three real roots, two of which sum to 5. What is $$|A|$$?

<br>

**Solution:** Let $$r_1, r_2$$ be the roots that sum to 5. This must mean $$r_3 = -5$$, since $$r_1 + r_2 + r_3 = 5 - 5 = 0$$ (there is no $$x^2$$ term).

We also know $$r_1r_2r_3 = - 15$$. Then,

<div align=center>

$$\begin{aligned} -A &= r_1r_2 + r_1r_3 + r_2r_3  = r_3(r_1 + r_2) + r_1r_2 \\\ &= r_3(r_1 + r_2) + \frac{r_1r_2r_3}{r_3} \\\ &= -5(5) + \frac{-15}{-5} = -25 + 3 = -22 \end{aligned}$$

</div>

Thus, $$\boxed{|A| = 22}$$.

<br>

### Example 3
---

Suppose the polynomial $$f(x) = x^3 − \alpha x^2 + \beta$$ has three roots, one of which is equal to $$\beta^2$$. What is the sum of all possible values of $$\beta$$? _(Hint: There is both an easy way and hard way to reason about this. Vieta's formulas aren't necessary involved.)_

<br>

**Solution 1:** First, let's do this using Vieta's formulas.


**Solution 2:** Now, let's reason about this using the remainder theorem (which, again, you can read about in 5.4). If $$\beta^2$$ is a root, then $$f(\beta^2) = 0$$. 

<div align=center>

$$\begin{aligned} f(\beta^2) &= 0 \\\ \beta^6 - \alpha \beta^4 + \beta &= 0 \end{aligned}$$

</div>

This is the same polynomial as we saw in the first method just above. The sum of the roots of $$\beta$$ here, again, is $$\boxed{0}$$.


<br>

### Example 4
---

Let $$f(x) = (x^2 + 6x + 9)^{50} - 4x + 3$$, and suppose $$f(x)$$ has 100 roots, $$r_1, r_2, r_3, ..., r_{100}$$.  Determine $$(r_1 + 3)^{100} + (r_2 + 3)^{100} + ... + (r_{100} + 3)^{100}$$.


<br>

**Solution:** All roots $$r_i$$ must satisfy $$(x^2 + 6x + 9)^{50} - 4x + 3 = 0$$, i.e. $$(x + 3)^{100} = 4x - 3$$. Taking the sum over all roots $r_i$ on both sides:

<div align=center>

$$\begin{aligned} \sum_{i = 1}^{100} (r_i + 3)^{100} &= \sum_{i = 1}^{100} (4r_i - 3) \\\ &= 4 \sum_{i = 1}^{100}r_i - 300 \end{aligned}$$

</div>

Now, we just need to find the sum of the roots $$r_i$$. Using the _binomial theorem_, we find the coefficient of the second term of $$(x+3)^{100}$$ to be $${100 \choose 1}3 = 300$$, meaning the sum of the roots is $$-300$$. Then:

<div align=center>

$$\sum_{i = 1}^{100} (r_i + 3)^{100} = 4 \cdot (-300) - 300 = \boxed{-1500}$$

</div>
