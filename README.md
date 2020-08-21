# The Little Typer

Here is a repo for my notes and the like while reading through *The Little Typer* by Daniel P. Friedman and David T. Christiansen.

The book introduces and explores dependent types using **Pie**, a small dependently typed language.

To run these files, you need to:
- install Racket
- open DrRacket
- install Pie from the packages

## Types

To understand dependent types, it is important to understand what a type is.

Typically, types start with a capital letter. They look like `Atom` or `Nat`. A type is something that has a constructor and an eliminator.

For `Nat`, which is the type for a natural number, has one constructor: `zero`.
For eliminators, `Nat` only has `add1`.

We can
```
(claim one Nat)
```
or "Claim one to be the type Nat."

Then
```
(define one
  (add1 zero))
```

Easy enough, right?
