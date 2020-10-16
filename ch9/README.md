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
