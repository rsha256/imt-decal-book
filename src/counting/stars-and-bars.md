<title>Stars and Bars – IMT DeCal</title>

# Counting Technique: Stars and Bars

_by Suraj Rampure_<br>
_Last modified: March 21, 2019_

---

<br>

<!--

Jump to: 
- [Introduction](#introduction)
- [Generalization](#generalization)
- [Algebraic Formulation](#algebraic)
    - [Adding Constraints](#constraints)

<br>

-->

<a name="introduction">

## Introduction
---

</a>

<br>

The typical stars-and-bars problem is usually of the form

<div align=center>

**Suppose I have 20 one-dollar bills, and want to distribute them amongst my three closest friends. How many ways can I do this?**

</div>

This sounds like a counting problem, so let’s try and model this in a way that will allow us to use what we know about permutations and combinations. 

Let's suppose I lay all 20 of my dollar bills out in a line, side-by-side. In order to split the money amongst my three friends, I could split the line of 20 dollars into three parts. Everything in the first part goes to my first friend, everything in the second part goes to my second friend, and everything in the third part goes to my third friend. I only need two dividers to do this — one to divide between my first and second friend, and another to divide between my second and third friend.

We can treat each dollar as a “star”, with the symbol $$*$$. Since I have three friends, I have two “dividers”, which I can refer to as “bars”, with the symbol $$|$$. My problem now boils down to determining the number of _permutations_ of 20 stars and 2 bars, i.e. the number of permutations of $$********************||$$. Each permutation of this string represents a different configuration. 

For example:
- $$*****|***|************$$ represents the situation where my first friend gets 5 dollars, my second friend gets 3 dollars, and my third friend gets 12 dollars.
- “$$************|*****|***$$” represents the situation where my first friend gets 12 dollars, my second friend gets 5 dollars, and my third friend gets 3 dollars. Notice that even though the numbers in the second example are the same, this represents a different distribution of the dollars to my friends and hence is counted separately). 
- “$$|**|******************$$” represents the situation where my first friend receives nothing, my second friend receives 2 dollars, and my third friend receives 18 dollars. Notice that for now, we are fine with one of my friends receiving no money. (What if we want to ensure that everyone receives at least one dollar? Keep on reading!)

The number of permutations of the string $$********************||$$ is

<div align=center>

$${22 \choose 2} = \frac{22!}{20! 2!} = 231$$

</div>

We can reason about this in two slightly different ways:

1. Recall, when we found the number of permutations of MISSISSIPPI earlier in the chapter, we found that the number of permutations of a string is the factorial of the number of total characters, divided by the product of the factorials of the quantity of each repeating character. In the MISSISSIPPI example, this evaluates to $$\frac{11!}{4! 4! 2!}$$, and in our case, since we have 22 total characters, with 2 repeated “$$|$$” and 20 repeated “$$*$$”, our result is $$\frac{22!}{20!2!}$$.
2. In total, there are 22 characters in this string. We want to choose 2 of them to be bars, or equivalently, 20 of them to be stars. This can be done in $${22 \choose 2} = {22 \choose 20}$$ ways.

Both interpretations yield the same result. Let’s now generalize, to any number of dollars and any number of friends. Notice, we had 20 stars and 2 bars, and our result ended up being $${stars + bars \choose stars}$$ which can also be written as $${stars + bars \choose bars}$$.

<br>

<a name="generalization">

## Generalization
---

</a>

<br>

When we want to distribute $$n$$ **indistinguishable objects** (dollars) into $$k$$ **distinguishable bins** (people), we can model our problem using $$n$$ **stars** and $$k-1$$ **bars**. The number of ways this can be done is

<div align=center>

$$\boxed{{n + k - 1 \choose n}}$$ or $$\boxed{{n + k - 1 \choose k-1}}$$

</div>

Or, equivalently,

<div align=center>

$$\boxed{{stars + bars \choose stars}}$$ or $$\boxed{{stars + bars \choose bars}}$$ 

</div>

Since $${a + b \choose a} = {a + b \choose b}$$, these representations are identical.

<br>

<a name="algebraic">

## Algebraic Formulation
---

</a>

<br>

Suppose I want to find the number of non-negative integer solutions (i.e., $$x_i \in \mathbb{N}_0$$) to 

<div align=center>

$$x_1 + x_2 + x_3 + x_4 + x_5 = 100$$

</div>

This is actually the exact same problem as we saw above! We can model this using stars and bars, with 100 “stars” and 4 “bars." You can think of the addition signs as being the bars. Here, using the general formula defined above, we have $${104 \choose 4}$$ solutions.

**In general, the equation $$\sum_{i = 1}^k x_i = n$$ has $${n + k - 1 \choose k - 1}$$ non-negative integer solutions.**

<br>

<a name="constraints">

### Adding Constraints
---

</a>

<br>

Let’s make things slightly more interesting. How can we find the number of **positive** integer solutions to $$x_1 + x_2 + x_3 + x_4 + x_5 = 100$$, i.e. where all values are non-zero?

In the non-negative case, we had that each $$x_i \geq 0$$. Now, we want $$x_i > 0$$, or equivalently, $$x_i \geq 1$$ (this is true because in both cases, we are confined to the larger set of integers). To account for this, we can define $x_i' = x_i - 1$. Now, the only constraint we have is $x_i' \geq 0$, which we already know how to solve, from the above formulation.

<div align=center>

$$x_1 + x_2 + x_3 + x_4 + x_5 = 100$$

$$(x_1 - 1) + (x_2 - 1) + (x_3 - 1) + (x_4 - 1) + (x_5 - 1) = 100 - 5$$

$$x_1' + x_2' + x_3' + x_4' + x_5' = 95$$

</div>

In our new equation, we have 95 stars and 4 bars, giving us $${99 \choose 4}$$ solutions to this equation, meaning that our original equation $$\sum_{i = 1}^5 x_i = 100$$ has $${99 \choose 4}$$ positive integer solutions.

**In general, the equation $$\sum_{i = 1}^k x_i = n$$ has $${n - 1 \choose k - 1}$$ positive integer solutions.**

<br>

The task of adding constraints to our problem isn't just restricted to the algebraic formulation --- let's tie this back into the problem of distributing 20 dollar bills. Suppose we want to distribute these dollar bills in a way that everyone receives at least one dollar. We can model this with $$x_1 + x_2 + x_3 = 20$$, such that $$x_i \geq 1$$, giving us $${20 - 1 \choose 3 - 1} = {19 \choose 2}$$ solutions.