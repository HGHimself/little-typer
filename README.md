# The Little Typer

Here is a repo for my notes and the like while reading through *The Little Typer* by Daniel P. Friedman and David T. Christiansen.

The book introduces and explores dependent types using **Pie**, a small dependently typed language.

To run these files, you need to:
- install Racket
- open DrRacket
- install Pie from the packages

## Types

A type is how you would categorize a "thing". It depends on the thing's form and nature. Normally you start with a small set of types and combine them into larger, more complex types. Some of the types available to us follow:
- Nat - all positive numbers and zero; a.k.a. a natural number
- Atom - any characters following a single quote, `'atom`, `'apple`, `'banana`
- Pair - two types grouped together with a designated order
- List - a homogenous, ordered group of types
- Vec - a homogenous, ordered group of types that has a specified length

Types have something called constructors. These are how you create a type to become or to be used in an expression. The constructors for Nat are `zero` and `add1`. The constructor for a Pair is `cons`.

Types also have something called eliminators. This is how you pull information out of a type. The eliminators for Pair are `car` and `cdr`, which give the first and second elements of the pair, respectively.

Using these two concepts, one can achieve very complex statements. Let us discuss what statements are.

## Statements

We can use the types above to claim that something exists. For example, I could claim that a Nat exists. In order to prove that I am correct, all I would need to do is provide a number, say 15. Maybe that is too simple to grasp so allow me to provide another example. I could claim that a `(Pair Nat Atom)` exists. In order to prove this, I can provide a `(cons 15 'apple)`.

This idea is what allows us to prove things. Imagine, if you will, a more complex type than just Pair. If we provide a value with this type, it is living proof that the type exists. That is, the type is a theorem of our system, is true in our system, or can be derived with our system.

The types provided above cannot say much in the way of things that are of interest.
