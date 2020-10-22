# Double Your Money, Get Twice as Much

We have just learned about `cong`. By the Law of `cong`, if *target* is an `(= X from to)` and *f* is an `(-> X Y)`,
then `(cong target f)` is an `(= Y (f from) (f to))`.

An ind-Nat-expression can have any type, it all depends on the motive. A cong-expression's type always has to have `=` at the top.

For a more general purpose eliminator, we introduce `replace`. If two expressions are equal, then whatever is true for one is true for the other. This is called Leibniz's Law.

### The Law of `replace`
If *target* is an `(= X from to)`, *mot* is an `(-> X U)`, and *base* is `(mot from)`
then `(replace taret mot base)` is a `(mot to)`.

The motive explains what is true for both expressions in Leibniz's Law. It is an`(-> X U)` because it explains how to find a *U* (and therefore a statement) from *X*.

The base is evidence that `(mot from)` is true. That is, the base's type is `(mot from)`.

Replace is used when something *nearly* fits. To explain it in my own words, it will help you map something to something else in a truth-y fashion. When given an =-expression of type `(= X from to)`, we can be sure the equality is true (since the value would not exist otherwise). The replace is built up with a motive and a base of types `(-> X U)` and `(mot from)` respectively. This means we have motive being a mapper/wrapper that will convert our equality into another type. In order to be consistent and remain true, we provide an expression with the type of the motive applied to the aforementioned `from`. The existence of the base tells us the motive can be applied to the `from`. We know `from` and `to` are equal, so we can easily deduce that `(mot to)` is true as well. This is what the whole replace expression resolves to.

### The Law of `symm`
If *e* is an `(= X from to)`, then `(symm e)` is an `(= X to from)`.

### The Commandment of `symm`
If *x* is an *X*,
then `(symm (same x))` is the same `(= X x x)` as `(same x)`.
