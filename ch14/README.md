# There's Safety in Numbers

What if we were to select an out-of-bounds element from a list? We need a new type to express this, called `Trivial`. `Trivial` is sometimes called the unit type.

### The Law of Trivial
`Trivial` is a type.

### The Law of `sole`
`sole` is a `Trivial`

### The Commandment of `sole`
If *e* is a `Trivial`, then *e* is the same as `sole`.

### The Law of `Absurd`
`Absurd` is a type.

There are no values of `Absurd`, and all of them are the same. In fact, *every* expression that is an `Absurd` is the same as every other expression that is an `Absurd`. If there are no values, then there is no way to tell any of them apart.

If there are no `Absurd` values, how can there be expressions of type `Absurd`? Neutral expressions are just that. Look at `similarly-absurd` in the code file for this chapter.

### The Commandment of Absurdities
Every expression of type `Absurd` is netureal, and all of them are the same.

Even thought there is no way to construct an `Absurd` value, there is an eliminator for `Absurd`. One way to view an eliminator is as a means of exposing the information inside a constructor. Another way to view it is as a way of picking some new expression for each of a type's values.

- `length` picks a new `Nat` for each `List`.
- `peas` picks a `(Vec Atom l)` for each `Nat l`.

By picking a new expression for each value, the eliminator expression itself has a type given by the motive. To use the eliminator for `Absurd`, provide a new expression for each `Absurd` value. But there are no absurd values.

The eliminator for `Absurd` is `ind-Absurd` and it has neither bases not steps because there are no `Absurd` vales. There is only a target and a motive.

### The Law of `ind-Absurd`
The expression `(ind-Absurd target mot)` is a *mot* if *target* is an `Absurd` and *mot* is a `U`.

The purpose for `ind-Absurd` is to express that some expressions can never be evaluated, or in other words, that the expression is permanently neutral. This is useful when you need a type but you know it is not possible. For example, consider an ind-Vec-expression that never uses the base, even though a base is required in the expression definition. It is possible to use an ind-Absurd expression that will fulfill the correct type of the base while making it impossible to ever be used. Here is an example from the next chapter:
```
(claim absurd-base
  (Pi ((E U)
       (j Nat))
    (-> (= Nat 0 (add1 j))
        (Vec E j))))

(define absurd-base
  (lambda (E j eq)
    (ind-Absurd
      (zero-not-add1 j eq)
      (Vec E j))))
```
There is nothing that will ever fit into the target of the ind-Absurd expression here. The type of it is, invariably, `(Vec E j)` regardless of whether it will ever be used. This keeps the outer definition of the ind-Vec happy.
