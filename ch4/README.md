# Easy as Pie

- `(Pair Nat Nat)` is an expression and has an eliminator
- `(Pair Nat Atom)` is an expression and also has an eliminator

This implies that there are lots of eliminators for `Pair`, because it is always possible to  nest them more deeply.

It is possible to provide an eliminator for and `(Pair A D)`, *no matter what A and D are*.

To eliminate a pair of any types, we need some sort of variables that accept the types we wish to work with. Consider the following:

```
(-> A D
  X
  (Pair A D)
  (-> A D
    X)
  X)
```
- *A*, *D*, and *X* are the first three arguments, the fourth argument is a `(Pair A D)`, and the fifth argument is *X* which the whole thing resolves to.

Names that occur in an expression must refer to either a definition or to an argument named by a lambda. There is clearly no lambda in that expression, and neither *A* nor *D* not *X* are defined.

Recall what it means to be an `(-> Y X)`. An `(-> Y X)` is a lambda-expression that, when given a *Y*, results in an *X*. It can also be an expression whose value is sucj a lambda-expression.

*Y* and *X* are types.

The issue at hand is that these placeholders for types need either to be defined to be a type or to do something else.

Enter `Pi`. Both `Pi` and `->` are used to describe lambda-expressions.

When an expression is described by a pi-expression is applied, the argument expressions replace the *argument names* in the *body* of the pi-expression.

In the following pi-expressions:
```
(Pi ((A U)
     (D U))
  (-> (Pair A D)
    (Pair D A)))
```
the argument names are *A* and *D*. Pi-expressions can have one or more argument names, and these argument names can pccur in the body of the pi-expressions. The body is a `(-> (Pair A D) (Pair D A))`. It is the type of the lambda expression that is described by the body of the pi-expression.

### The Intermediate Law of Application
If *f* is a `(Pi ((Y U)) X)` and *Z* is a *U*,
then `(f Z)` is and *X* where every *Y* has been consistently replaced by *Z*.

To be a `(Pi ((Y U)) X)` is to be a lambda-expression that, when applied to a type *T*, results in an expression with the type that is the result of consistently replacing every *Y* in *X* with *T*. It can also be an expression *whose value is* such a lambda-expression.
