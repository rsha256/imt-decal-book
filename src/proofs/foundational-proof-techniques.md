<title>Foundational Proof Techniques – IMT DeCal</title>

# Foundational Proof Techniques

_by Fahad Kamran, Suraj Rampure_<br>
_Last modified: March 21, 2019_

---

<br>

<!--

Jump to:
* [Direct Proof](#direct)
* [Proof by Contradiction](#contradiction)
	* [Contradicting Implications](#contradictimplication)
* [Proof by Contraposition](#contraposition)
* [Example: Proving If and Only If](#iffproofs)
* [Proof by Cases](#cases)
* [Counterexamples and Vacuous Proofs](#counter_vacuous)
	* [Counterexamples](#counterexamples)
	* [Vacuous Proofs](#vacuous)
* [Faulty Proofs and Logic](#faulty)

<br>

-->


Throughout this note, we will introduce some of the more common proof techniques that are used to verify the truth of a mathematical statement. Remember, all of these techniques assume you have some basic information present and attempt to use the information you have to arrive at the correct conclusion. It's important that you're familiar with the basics of **[propositional logic](../sets/propositional-logic.html)** before proceeding. 

In this article, we'll introduce the symbol for "divides". $$a | b$$ means "$$a$$ divides $$b$$". Formally, $$a | b$$ means there is some integer $$c$$ such that $$b = c \cdot a$$; in other words, this means $$b$$ is an integer multiple of $$a$$. For example, we could say $$8 | 24$$, but $$\neg (5  | 24)$$. 

Additionally, we often use $$2k$$, $$k \in \mathbb{Z}$$, to refer to an arbitrary even number, and $$2k + 1$$ to represent an arbitrary odd number. This means all integers can be written as either $$2k$$ or $$2k + 1$$. Similarly, we can say all integers can be written as $$3k$$, $$3k + 1$$ or $$3k + 2$$, where $$0, 1, 2$$ represent the possible remainders when we divide by 3. This is an idea we will study further when we get to number theory.

But first – what is a proof?

Formally, a mathematical **proof** is a finite sequence of valid steps which, when combined in a specific order, indicate the truth of a specific statement. Though, we don't need to be so formal – at its core, **a proof is an argument to convice someone that a statement is true.**

<br>

<a name='direct'>

## Direct Proof
---

</a>

The direct proof is the simplest type of proof. In a direct proof, given certain information, we determine the validity of some other information. Direct proofs are often used in mathematical formulas, where simple arithmetic manipulations of given information can get us where we need to be. 

#### Example

**Consider $$x, y, z \in \mathbb{Z}^+$$. Prove that if $$x | y$$ and $$x | z$$, then $$x | (y + z)$$.**

The first step in each proof is representing the information that we are allowed to assume, using precise mathematical notation. We are given that $$x$$ divides $$y$$ and that $$x$$ divides $$z$$. In mathematical notation, this means that there are integers $$a_1$$ and $$a_2$$ such that $$a_1 \cdot x = y$$ and $$a_2 \cdot x = z$$. Furthermore, since we are told $$x, y$$ and $$z$$ all belong to the set of positive integers, we know that $$a_1, a_2$$ must also be positive. There is not much more information we can garner from this now, so we look at what we are trying to prove.

By writing out equations relating $$x$$ and $$y$$ (and $$x$$ and $$z$$), we have concrete information that we can use in our proof. Then:

<div align=center>

$$
y+z = a_1 \cdot x + a_2 \cdot x = (a_1 + a_2) \cdot x
$$

</div>

We have shown that $$y+z$$ can be written as some positive integer – precisely, $$a_1 + a_2$$ – multiplied by $$x$$. Therefore, we have proven that under the given conditions, $$x | (y + z)$$.


This example gives us the natural flavor of direct proofs – we assume and work with the information we have, and reformulate it to match what we want to prove in some capacity.

<br>

#### Example

**Prove that $$\forall n \in \mathbb{N}, 3 | (n^3 - n)$$.**

Essentially, we're required to show that we can write $$n^3 - n = 3k$$, where $$k$$ is some integer. We can start by factoring $$n^3 - n$$:

<div align=center>

$$\begin{aligned} n^3 - n &= n(n^2 - 1) \\\ &= n(n - 1)(n + 1) \\\ &= (n-1)n(n+1) \end{aligned}$$

</div>

_In the second line, we used the difference of squares, which says $$x^2 - y^2 = (x-y)(x+y)$$._

Now, we've written $$n^3 - n$$ as the product of three consecutive integers, starting with $$n - 1$$. A property that we can now leverage is the fact that in any three consecutive integers, one of them will be a multiple of three! We will eventually get to a stage where we can rigorously prove this. Skipping ahead a little, though: let's consider the three possible cases for $$n$$:

- Case 1: $$n = 3k$$, meaning $$n$$ is a multiple of 3
- Case 2: $$n = 3k + 1$$, meaning $$n - 1 = 3k$$ is a multiple of 3
- Case 3: $$n = 3k + 2$$, meaning $$n + 1 = 3k + 3 = 3(k+1)$$ is a multiple of 3

Therefore, it is always the case that one of our three consecutive integers is a multiple of 3, and so the product $$(n-1)n(n+1)$$ will always be a multiple of 3. The only edge case that we need to look out for is $$n = 1$$, which gives $$n^3 - n = 0$$, but that's fine – every number divides 0, as we can say $$3 \cdot 0 = 0$$. 

Therefore, we can say $$3 | (n^3 - n)$$. 

_Note: You will notice in these proofs that we often have a concluding sentence. This is a good practice to follow._

<br>

<a name='contradiction'>

## Proof by Contradiction
---

</a>

Proofs by contradiction stem from a really nice observation. The problem statement remains the same; we are trying to prove that some statement $$S$$ is true. We begin by assuming $$\neg S$$ – that is, that $$S$$ is false - and make a series of implications. One of these implications will state something that contradicts that $$S$$ is false. Since our initial assumption was that $$S$$ was false, we know this cannot be the case (since $$S$$ and $$\neg S$$ cannot be equal), thus $$S$$ must be true, proving our statement.

The contradiction can come about in many ways. For example, showing two things that cannot be equal as equal – such as $$0 = 2$$ – or showing some given information (which was told to us to be true) is false if statement $$S$$ is false. Whatever the contradiction might be, this proof technique presents a relatively straightforward way to prove the validity of the statement without worrying about the specific reason why the statement it holds. In specific, proofs by contradiction are powerful when trying to prove a statement which implies non-existence of some entity.

#### Example

**Prove that there is no greatest even integer.**

Let's start by assuming that there is a greatest even integer. Let us call this greatest even integer $$m$$. Define $$n$$ to be $$m+2$$. Then, $$n$$ is an even integer and it is strictly greater than $$m$$. Hence, $$m$$ is not the greatest even integer, which contracts our earlier assumption. This means that there is no greatest even integer.

<br>

#### Example

**Prove that $$\sqrt{2}$$ is irrational**.

This is a classic example of a statement that is proved with a contradiction. Let's start by assuming that $$\sqrt{2}$$ is rational, meaning that we can write $$\sqrt{2} = \frac{a}{b}$$ for $$a, b \in \mathbb{Z}$$. Furthermore, let's assume that this is the reduced form of the fraction, i.e. that $$\text{gcd}(a, b) = 1$$ (this is a crucial step in the proof). Then:

<div align=center>

$$\begin{align*} \sqrt{2} &= \frac{a}{b} \\\ 2 &= \frac{a^2}{b^2} \\\ 2b^2 &= a^2 \end{align*}$$

</div>

Since we have $$a^2 = 2b^2$$, we know that $$a^2$$ must be even (as it can be written as $$2 \cdot (\text{some integer})$$). If $$a^2$$ is even, then we must have that $$a$$ is even (if you don't believe it, you can prove it yourself!). This means we can say $$a = 2k$$ for $$k \in \mathbb{Z}$$. Then:

<div align=center>

$$\begin{align*} 2b^2 &= (2k)^2 \\\ 2b^2 &= 4k^2 \\\ b^2 &= 2k^2 \end{align*}$$

</div>

Same logic applies: we now have that $$b^2$$ is even, and therefore $$b$$ is even.

_Stop for a moment: can you spot the contradiction?_

If both $$a, b$$ are even, then $$\text{gcd}(a, b)$$ is at least $$2$$. This contradicts what we stated earlier – we assumed that $$\text{gcd}(a, b) = 1$$. This implies that our original assumption was false, thus proving that $$\sqrt{2}$$ is indeed irrational.

<br>

#### Example

**Prove that in any set of $$n$$ real numbers, there is at least one number that is less than or equal to the mean.**

Again, let's proceed by contradiction. The contradiction of "there is at least one number" is "there is no number". Our statement then reads, "there is no number that is less than or equal to the mean", which we can rewrite (using De Morgan's Laws!) as "all numbers are greater than the mean."

Let's suppose our numbers are $$x_1, x_2, ... , x_n$$. Then, the mean is $$\frac{x_1 + x_2 + ... + x_n}{n}$$. If each $$x_i, \forall i \in [1, n]$$ is greater than the mean, we can then say 

<div align=center>

$$\begin{align*} x_1 &> \frac{x_1 + x_2 + ... + x_n}{n} \\\ x_2 &> \frac{x_1 + x_2 + ... + x_n}{n} \\\ &\vdots \\\ x_n &> \frac{x_1 + x_2 + ... + x_n}{n} \end{align*}$$

</div>

Taking the sum of both sides of the inequality:

<div align=center>

$$x_1 + x_2 + ... + x_n > x_1 + x_2 + ... + x_n$$

</div>

This is a contradiction! No number is greater than itself. This means our assumption was incorrect. Since our assumption was that there is no number less than or equal to the mean, we've proven that in a set of $$n$$ numbers there is at least one number less than or equal to the mean.


<a name="contradictimplication">

### Contradicting Implications
---

</a>

Just because our problem statement looks like an implication, doesn't mean we need to use a proof by contraposition. 

Our initial statement that we negate can also be an implication! Suppose we want to show that $$P \implies Q$$. This is equivalent to showing that $$\neg P \vee Q$$ is always true. To show a contradiction, we can start by assuming $$\neg (\neg P \vee Q)$$, i.e. $$P \wedge \neg Q$$, and showing a contradiction. 

#### Example

**Prove that if $$x^2$$ is even, then $$x$$ is even.**

We want to show that $$(x^2 \text{ is odd} \vee x \text{ is even})$$ always holds a true value. The negation of this looks like $$x^2 \text{ is even} \wedge x \text{ is odd}$$. 

If we assume the negation to be true, we have that $$x^2$$ is even and $$x \text{ is odd}$$. If we suppose $$x$$ is odd, we can write it as $$2k + 1, k \in \mathbb{Z}$$, and we can write $$x^2 = (2k + 1)^2 = 4k^2 + 4k + 1 = 2(2k^2 + 2k) + 1$$. This shows that we can write $$x^2$$ as $$2 \cdot (\text{some integer}) + 1$$. This proves that $$x^2$$ must be odd if $$x$$ is odd, meaning that the assumption $$x^2 \text{ is even} \wedge x \text{ is odd}$$ was false. Thus, the original statement $$(x^2 \text{ is odd} \vee x \text{ is even})$$, i.e. $$x^2 \text{ is even} \implies x \text{ is even}$$, is true. 

<br>

#### Example

**Prove that if $$A, B, C$$ are odd integers, then there are no rational solutions to $$ax^2 + bx + c = 0$$.**

The negation of this statement is "$$A, B, C$$ are odd integers and there exist rational solutions to $$ax^2 + bx + c = 0$$." Let's assume the negation to be true. 

If there are rational solutions, then we can factor $$ax^2 + bx + c$$ into $$(Ax + B)(Cx + D)$$ (implying that the two solutions are $$-\frac{B}{A}$$ and $$-\frac{D}{C}$$, but this isn't relevant to the problem). Then,

<div align=center>

$$\begin{align*} ax^2 + bx + c &= (Ax + B)(Cx + D) \\\ &= ACx^2 + (AD + BC)x + BD \end{align*}$$

</div>

This implies that we have the following equalities:

<div align=center>

$$\begin{align*} a &= AC \\\ b &= AD + BC \\\ c &= BD \end{align*}$$

</div>

Since $$a$$ is odd, this means that $$A$$ and $$C$$ are both odd. Similarly, since $$c$$ is odd, this means that $$B$$ and $$D$$ are both odd. Putting these facts together, we have that $$A, B, C, D$$ all must be odd.

Now, let's consider $$b = AD + BC$$. The products $$AD$$ and $$BC$$ are both odd, and when we add two odd numbers, our result is even. This means that $$b$$ must be even. This is a contradiction, since we assumed $$a, b, c$$ were all odd.

Therefore, by contradiction, we have that the proposition holds.


<br>

<a name='contraposition'>

## Proof by Contraposition
---

</a>

Recall from Chapter 1.4, the contrapositive of an implication $$P \implies Q$$ is $$\neg Q \implies \neg P$$. Implications and their contrapositives are logically equivalent statements. Contrapositives are useful in cases where we are asked to prove some statement $$Q$$ from some set of information $$P$$: instead of proceeding with a direct proof, we can instead assume that $$Q$$ is false ($$\neg Q$$) and make a series of logical deductions that imply that $$P$$ is false ($$\neg P$$). In many cases, this is easier to do than proving that $$P$$ implies $$Q$$ directly.


#### Example

**Prove that if $$x^2 - 6x + 5$$ is odd, then $$x$$ is even.**

First, we'll prove the statement directly. To proceed, we can factor $$x^2 - 6x + 5$$ into $$(x-1)(x-5)$$. If this product is odd, then each of $$x-1$$ and $$x-5$$ has to be odd (the only way for a product of two integers to be odd is if both integers are odd; this is a fact you can prove on your own). 

Now, if $$x - 1$$ is odd, we have that $$x$$ is even, since adding two odd numbers yields an even number. The same holds for $$x - 5$$. To be more rigorous, since $$x - 1$$ is odd, we can say $$x - 1 = 2k_1 + 1$$, where $$k_1 \in \mathbb{Z}$$. Then, $$x = 2k + 2 = 2(k + 1)$$, therefore $$x$$ is even. The same applies with $$x - 5$$: $$x - 5 = 2k_2 + 1 \implies x = 2k_2 + 6 = 2(k_2 + 3)$$ (note, we used two different $$k$$s, as both conditions need to be satisfied at the same time).

Therefore, if $$x^2 - 6x + 5$$ is odd, $$x$$ must be even.

<br>

Now, let's prove the statement using a proof by contraposition. The contrapositive of this statement is, "if $$x$$ is odd, then $$x^2 - 6x + 5$$ is even". If $$x$$ is odd, we can write $$x = 2k + 1$$ for $$k \in \mathbb{Z}$$. Then:

<div align=center>

$$\begin{align*} x^2 - 6x + 5 &= (2k+1)^2 - 6(2k + 1) + 5 \\\ &= 4k^2 + 4k + 1 - 12k - 6 + 5 \\\ &= 2(2k^2 - 4k) \end{align*}$$

</div>

We've shown that when $$x$$ is odd, $$x^2 - 6x + 5$$ can be written as $$2 \cdot (\text{some integer})$$, therefore by contraposition, the original statement holds.


<br>


<a name='iffproofs'>

## Example: Proving If and Only If
---

</a>

_Note: Proving statements of the form "if and only if" isn't a "proof technique" on its own._

When the statement that we're required to prove is of the form "$$P$$ if and only if $$Q$$", we essentially need to perform two separate proofs. We need to independently prove $$P \implies Q$$ (i.e. "if $$P$$, then $$Q$$"), and prove $$Q \implies P$$. For each of these separate proofs, we can use whichever proof technique we'd like.

#### Example

**Given $a, b, x, y \in \mathbb{N}$ such that $A = a + \frac{1}{x}$, $B = b + \frac{1}{y}$, $y$ divides $a$, and $x$ divides $b$, prove that the product of $A$ and $B$ is an integer if and only if $x = y = 1$.**

We need to prove both of the following (given the initial conditions):
- If $$x = y = 1$$, then the product $$AB$$ is an integer
- If the product $$AB$$ is an integer, then $$x = y = 1$$

Let's first prove the first statement (sometimes referred to as the "forward direction"). If $$x = y = 1$$, then $$A = a + 1$$ and $$B = b + 1$$ by subsitution. Then, we have

<div align=center>

$$\begin{align*} AB &= (a+1)(b+1) \\\ &= ab + a + b + 1 \end{align*}$$

</div>

The sum and product of several integers is also an integer. Therefore, we've proven the forward direction.

Now, let's prove the second statement, or the "reverse direction". Firstly, let's expand the product $$AB$$: 

<div align=center>

$$\begin{align*} AB &= (a + \frac{1}{x})(b + \frac{1}{y}) \\\ &= ab + \frac{b}{x} + \frac{a}{y} + \frac{1}{xy} \end{align*}$$

</div>

Using the initial condition that $y$ divides $a$ and that $x$ divides $b$, we know that $\frac{b}{x}$ and $\frac{a}{y}$ are both integers. Now, since the first three pieces of the above sum are integers, we just need to show that $$\frac{1}{xy}$$ is an integer.

Since $$x, y$$ are natural numbers, we have that $$x \cdot y \geq 1$$. If $$x \cdot y$$ is anything other than $$1$$, $$\frac{1}{xy}$$ will be a non-integer rational number between 0 and 1. Therefore, in order for $$\frac{1}{xy}$$ to be an integer, we need $$x \cdot y = 1$$, which (under the naturals) is only satisfied by $$x = y = 1$$. This proves the reverse direction.

Therefore, since we've proven both directions, we've proven the entire proposition. 

<br>

<a name='cases'>

## Proof by Cases
---

</a>

In many instances, we may find it easier to view a statement as the combination of many sub-cases. By proving each possible sub-case, we can prove the validity of the full statement. The technique we use for each sub-case can be any one of the above. This is a consequence of the following equivalance (which we also provide a truth table for):

<div align=center>

$$(P_1 \vee P_2) \implies Q \equiv (P_1 \implies Q) \wedge (P_2 \implies Q)$$

| $$P_1$$ | $$P_2$$ | $$Q$$ | $$(P_1 \vee P_2) \implies Q$$ | $$(P_1 \implies Q) \wedge (P_2 \implies Q)$$ |
| --- | --- | --- | --- | --- |
| T | T | T | T | T |
| T | T | F | F | F | 
| T | F | T | T | T |
| T | F | F | F | F |
| F | T | T | T | T |
| F | T | F | F | F | 
| F | F | T | T | T |
| F | F | F | T | T |

</div>

What's important is that our cases cover all of the possible variables under consideration. Otherwise, we don't have a complete proof!

#### Example

**Prove that the cube of any integer is either a multiple of 9, 1 more than a multiple of 9, or one less than a multiple of 9.**

The cases we break this proof into may seem rather arbitrary, but the more we practice this sort of proof, the more natural it will seem. Our proof revolves around the fact that when dividing an integer by 3, there are 3 possible remainders – 0, 1, or 2. We can write every integer as either $$3k$$, $$3k + 1$$ or $$3k + 2$$.

- _Case 1_: $$n = 3k$$ <br>
First, we look at numbers that are divisible by 3, which we can represent as $$3k$$ for some positive integer $$k$$. Cubing $$n$$, we get $$n^3 = (3k)^3 = 27k^3 = 9(3k^3)$$. Clearly, for all $$k$$, this is a multiple of $$9$$, therefore we've proved the statement for all integers that are multiples of 3.

- _Case 2_: $$n = 3k + 1$$ <br>
Next, we explore the case where there is a remainder of 1 after dividing by 3, so the number is $$3k + 1$$ for some $$k$$. Cubing $$n$$ yields $$n^3 = (3k+1)^3 = 27k^3 + 27k^2 + 9k + 1 = 9(3k^3 + 3k^2 + k) + 1$$, which shows that in this case $$n^3$$ is 1 greater than a multiple of 9. Thus, we've proved the statement for all integers that have remainder 1 when divided by 3.

- _Case 3_: $$n = 3k + 2$$ <br>
The last case is when a number has a remainder of 2 when being divided by 3. This means we can write $$n$$ as $$3k+2$$; equivalently, we can write $$n$$ as being 1 less than a multiple of 3, i.e. $$n = 3k - 1$$ (think about why this is true). Then, $$n^3 = (3k-1)^3 = 27k^3 - 27k^2 + 9k - 1 = 9(3k^3 - 3k^2 + k) - 1$$, which shows in this case that $$n^3$$ is 1 less than a multiple of 9. Now, we've proved the statement for all integers that have remainder 2 when divided by 3.

We have considered three cases, and these three cases make up the whole universe of integers. Either an integer is divisible by 3, one more than a multiple of 3, or 2 more than a multiple of 3 (and consequently, 1 less than some other multiple of 3). The statement holds for these three cases, so it holds for every integer. 

<br>

<a name='counter_vacuous'>

## Counterexamples and Vacuous Proofs
---

</a>

We've now covered the foundational proof techniques that we need to (other than induction, which we will look at next). Now, we'll look at a few oddities and things to note regarding proofs.

<a name='counterexamples'>

### Counterexamples
---

</a>

"Proof by Counterexample" isn't a proof technique. Instead, we use counterexamples to show that statements aren't true. For example, to prove that not all dogs are labradors, we would have to show there exists at least one dog that isn't a labrador. 

#### Example

**Prove or disprove: All Pythagorean triplets are of the form $$(3k, 4k, 5k)$$ for $$k \in \mathbb{R}$$.**

Consider the triplet $$(8, 15, 17)$$. We have that $$8^2 + 15^2 = 17^2$$, but $$(8, 15, 17) \neq (3k, 4k, 5k)$$ for any real number $$k$$. This is a counterexample, so the original statement is not true. 

<br>

<a name='vacuous'>

### Vacuous Proofs
---

</a>

Remember, implications are nothing but logical expressions with a _truth value_. By proving an implication, we are proving that the truth value of an implication is true. Many of the proof statements that we've seen so far require us to prove something of the form $$P \implies Q$$, and we assume that $$P$$ is true. The only way for $$P \implies Q$$ to have a value of true when $$P$$ is true, is for $$Q$$ to be true.

<div align=center>

| $$P$$ | $$Q$$ | $$P \implies Q$$ | $$\neg P \vee Q$$ |
| ---   | ---   | ---              | ---               |
| T | T | T | T |
| T | F | F | F |
| F | T | T | T |
| F | F | T | T |

</div>

However, the implication $$P \implies Q$$ is also true whenever $$P$$ is false. Consider the following statement:

<div align=center>

_If the earth is flat, then all dogs can fly._

</div>

The truth value of this implication, is true! This is because the earth is certainly not flat. If we let $$P$$ represent "the earth is flat" and $$Q$$ represent "all dogs can fly", since $$P$$ is false, it doesn't matter what $$Q$$ is: $$P \implies Q$$ is a true value.

One way to think of this is, if the left hand side $$P$$ is true, the laws of our universe don't hold. But if the laws of our universe don't hold, then anything is possible – it doesn't matter if $$Q$$ is true or false.

#### Example

**Prove that if $$2x^2 - 4x + 2 < 0$$, for $$x \in \mathbb{R}$$, then $$5 > 7$$.**

Usually, we assume the left hand side to be true, but let's look a little further here. The quadratic $$2x^2 - 4x + 2$$ can be written as $$2(x-1)^2$$, which sits on the $$x$$-axis. Therefore, it has a minimum value of $$0$$, and is never less than $$0$$. This means the left hand side is always false, thus the implication is always true.

This may seem a little confusing – we're not proving $$5 > 7$$. We're only showing that if $$2(x-1)^2 < 0$$ (for some real $$x$$), then $$5 > 7$$, i.e. that the implication holds.

<br>

<a name='faulty'>

## Faulty Proofs and Logic
---

</a>

Here are some common flaws to look out for in proofs:

- Assuming what we are trying to prove
-   Dividing by something which could be 0
-   Not switching inequalities when working with negative numbers
-   Using an example as a proof for a statement which applies to multiple cases
-   Introducing a variable twice with two different values

Let's look at a few examples.

#### Example

**Prove $$1 = 2$$**. 

Proof: Let $$x = y$$. Then:

<div align=center>

$$\begin{align*} x^2 &= xy \\\ x^2 - y^2 &= xy - y^2 \\\ (x+y)(x-y) &= y(x-y) \\\ x + y &= y \\\ 2y &= y \\\ 2 &=1 \end{align*}$$
</div>

_**Where did we go wrong?**_
- Since $$x = y$$, $$x - y = 0$$. From the third to fourth line, we divided by $$0$$, which is not a valid step.
- In the second last step, to solve $$2y = y$$, we were supposed to re-arrange so that we have $$y$$ on one side. What we did, dividing by $$y$$, is problematic as $$y$$ could've been $$0$$.

<br>

#### Example

**Prove that if $$n$$ is an integer and $$2n + 2$$ is even, then $$n$$ is odd.**

_Proof: Proceed by contraposition. Assume that $n$ is odd. We will now prove that $$2n + 2$$ is even. Clearly, $$2n$$ must be an even number, since it is divisible by $$2$$. Furthermore, 2 is an even number, so $$2n + 2$$ must be even. This concludes the proof._

_**Where did we go wrong?**_ Here, we did took the converse, instead of the contrapositive. "Proof by converse" is not a proof technique. If we actually took the contrapositive, which states "if $$n$$ is even, then $$2n + 2$$ is odd", we would see that it's impossible to show $$2n + 2$$ to be odd, as it is the sum of two even numbers.

<br>

#### Example

**Prove that 1 is the greatest whole number.**

_Proof: Let $$n \in \mathbb{N}$$ be the greatest whole number. Since it is the largest, its square $n^2$ must be less than or equal to it. We can then say $$n^2 \leq n$$, or equivalently, $$n(n-1) \leq 0$$. This inequality has two whole solutions, $$n = 0$$ and $$n = 1$$. Since $$1 > 0$$, we have that $n$ is the greatest whole number._

_**Where did we go wrong?**_ Here, we assumed the existence of a greatest whole number, which is not true.

<br>

Some of these examples may have more obvious flaws than others. In practice, though, flaws in proofs may not be as easy to spot.

<br>

In closing, there are (almost always) multiple ways to prove any one proposition. They may all use the same "proof technique" from the above, but use the given information differently. In the next article, we will round out our proof toolbox with a more involved proof technique – mathematical induction. 
