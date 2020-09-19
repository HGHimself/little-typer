# It All Depends on the Motive

How can we define a type that has as many elements in a vector that we require?

Imagine we have the following claim:
```
(claim peas
  (Pi ((how-many-peas Nat))
    (Vec Atom how-many-peas)))
```

How would we define `peas`?
```
(define peas
  (lambda (how-many-peas)
    (rec-Nat how-many-peas
      vecnil
      (lambda (l-1 peasl-1)
        (vec:: 'pea peasl-1)))))
```
We cannot use `rec-Nat` like above because of what we learned in chapter 3. Recalling, the base must hace rthe same type as the almost-answer argument to the step. Here, we would have a `(Vec Atom 29)` but `vecnil` is a `(Vec Atom 0)`. We need something more powerful for this *dependent type*.

### Dependent Types
A type that is determined by something that is not a type is called a *dependent type*.

For this, we will introduce `ind-Nat` with a new argument called the *motive*. The motive can be any `(-> Nat U)`.

### Use `ind-Nat` for Dependent Types
Use `ind-Nat` instead of `rec-Nat` when the `ind-Nat`- or `rec-Nat`-expression's type depends on the target `Nat`. the `ind-Nat`-expression's type is the motive applied to the target.

If the motive is called *mot*, then the step's type is
```
(Pi ((n-1 Nat))
  (-> (mot n-1)
    (mot (add1 n-1))))
```

Let's break this down. We use the *Pi* to assign a name to the Nat-type argument. The step becomes an arrow function where the singular argument is the motive applied to this named Nat. It evaluates to the motive applied to n. Imagine, if you will, this being a mapper to get from n-1 to n.

### The Law of `ind-Nat`
If *target* is a `Nat`, *mot* is an `(-> Nat U)`, *base* is a `(mot zero)`, and *step* is a
```
(Pi ((n-1 Nat))
  (-> (mot n-1)
    (mot (add1 n-1))))
```
then `(ind-Nat target mot base step)` is a `(mot target)`.

### The First Commandment of `ind-Nat`
The `ind-Nat` expression `(ind-Nat zero mot base step)` is the same `(mot zero)` as *base*.

### The Second Commandment of `ind-Nat`
The `ind-Nat` expression `(ind-Nat (add1 n) mot base step)` and `(step n (ind-Nat n mot base step))` are the same `(mot (add1 n))`.

### Induction on Natural Numbers
Building a value for any natural number by giving a value for zero and a way to transform a value for *n* into a value for *n* + 1 is called *induction on natural numbers*.

### `ind-Nat`'s Base Type
In `ind-Nat`, the base's type is the motive applied to the target *zero*.

### `ind-Nat`'s Step Type
In `ind-Nat`, the step must take two arguments, some `Nat n` and an almost-answer whose type is the motive applied to *n*. The type of the answer from the step is the motive applied to `(add1 n)`. The step's type is:
```
(Pi ((n Nat))
  (-> (mot n)
    (mot (add1 n))))
```

In prose, this means step transforms a function *f* for *l* into a function *f* for *(add1 l)*.
