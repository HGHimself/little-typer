# Eliminate All Natural Numbers!

Remember that recursion is not an option because recursion is not an option.

`gauss` is recursive and returns a value every time, but some recursion does not.

- The normal form of `(gauss 0)` is `zero`
- The normal form of `(gauss 1)` is `1` because of the following
```
(gauss (add1 zero))
(+ 1 (gauss zero))
(add1 (gauss zero))
```
Which is the value. To get the normal form we continue...
```
(add1 (gauss zero))
(add1 zero)
```

- `(gauss 2)` has a normal form
This is because `(gauss 2)`'s normal form relies only on the normal form of `(gauss 1)` and `+`. Both of these have normal forms, making the full expression have a normal form as well.

**Reminder**: An expression is normal only if all sub-expressions are normal as well.

- `(gauss 3)` has a normal form
This is because `(gauss 3)`'s normal form relies only on the normal form of `(gauss 2)` and `+`.

- `(gauss (add1 k))` has a normal form
This is because `(gauss (add1 k))`'s normal form relies only on the normal form of `(gauss k)` as well as the normal form of `+`.

`k`'s value is either `zero` or have `add1` at the top. `(gauss 0)` has a normal form and we ajust checked that `(gauss (add1 k))` has a normal form for any `Nat k`.

## Total Function
A function that always assigns a value to *every* possible argument is called a *total function*.

All functions in `Pie` are total. Because of this, it does not matter the order in which subexpressions get evaluated. If this was not the case, the order of evaluation would matter because it would determine whether or not functions were applied to the arguments for which they did not have values.

## The Law of `iter-Nat`
If a *target* is a `Nat`, *base* is an `X`, and *step* is an `(-> X X)`,
then `(iter-Nat target base step)` is an `X`.

## The First Commandment of `iter-Nat`
If `(iter-Nat zero base step)` is an `X`,
then it is the same `X` as *base*.

## The Second Commandment of `iter-Nat`
If `(iter-Nat (add1 n) base step)` is an `X`,
then it is the same `X` as `(step (iter-Nat n base step))`.

- The normal form of `(iter-Nat 5 3 (lambda (smaller) (add1 smaller)))` is 8

The `iter-Nat` expression is the same type as *base*.

- *base* is an `X`
- *step* is applied to *base*
- *step* is applied to an almost-answer built by *step*

*step* is an `(-> X X)`.

`iter-Nat` is not powerful enough to define `gauss`, even though `iter-Nat` allows us to successively eliminate the smaller `Nat` tucked under the `add1`.

We need to use `rec-Nat`, which gives us two arguments to the step function: the almost-answer and the value of the `rec-Nat` applied recursively to the almost-answer.

The step function for `rec-Nat` is `(-> Nat X X)`.
