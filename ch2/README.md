# Doin' What Comes Naturally

- `car` is an *eliminator*
- `cdr` is an eliminator

### Constructors and Eliminators
Constructors build values, and eliminators take apart values build by constructors.

Values contain information; eliminators allow that information to be used.

There is nothing that is both a constructor and an eliminator.

`lambda` is the constructor for a function.

### Eliminating Functions
Applying a function to arguments is the eliminator for functions.

- `(lambda (flavor) (cons flavor 'lentils))` is a value
- The value of `(lambda (flavor) (cons flavor 'lentils) 'garlic)` is `'garlic`

To be an `(-> Atom (Pair Atom Atom))` is to be a lambda expression that, applied to an Atom as its argument, evaluates to a `(Pair Atom Atom)`.

Two expressions are the same `(-> Nat Atom)` when their values are the same `(-> Nat Atom)`.

Two lambda-expressions that expect the same number of arguments are the same if their bodies are the same.

### The Initial Law of Application
If `f` is an
```
(-> Y
  X)
```
and `arg` is a `Y`, then
```
(f arg)
```
is an `X`.

### The Initial First Commandment of `lambda`
Two `lambda`-expressions that expect the same number of arguments are the same if their bodies are the same after consistently renaming their variables.

### The Initial Second Commandment of `lambda`
If `f` is an
```
(-> Y
  X)
```
then `f` is the same
```
(-> Y
  X)
```
as
```
(lambda (y)
  (f y))
```
as long as y does not occur in `f`.

### The Law of Renaming Variables
Consistently renaming variables can't change the meaning of anything.

Expressions that are not values and cannot *yet* be evaluated due to a variable are called *neutral*.

- `(cons y 'rutabaga)` is a value
- If x is a `(Pair Nat Atom)`, `(cdr x)` is neutral

Neutral expressions make is necessary to expand our view of what it means to be the same.

- `(lambda (x) (car (cons x x)))` is the same `(-> Nat Nat)` as `(lambda (x) x)`.
- `(lambda (x) (car x))` is the same `(-> (Pair Nat Nat) Nat)` as `(lambda (y) (car y))`

### The Commandment of Neutral Expressions
Neutral expressions that are written identically are the same, *no matter their type*.

### The Law and Commandment of `define`
Following `(claim name X)` and `(define name expr)`,
if `expr` is an `X`,
then `name` is an `X` and `name` is the same `X` as `expr`.

### The Second Commandment of `cons`
If `p` is a `(Pair A D)`, then it is the same `(Pair A D)` as `(cons (car p) (cdr p))`.

`which-Nat` is an eliminator for `Nat` that can distinguish between `Nat`s whose values are `zero` and `Nat`s whose values have `add1` at the top.

The value of
```
(which-Nat zero
  'naught
  (lambda (n)
    'more))
```
is `'naught`


The value of
```
(which-Nat 4
  'naught
  (lambda (n)
    'more))
```
is `'more`

### The Law of `which-Nat`
If `target` is a `Nat`, `base` is an `X`, and `step` is an `(-> Nat X)`,
then
```
(which-Nat target
  base
  step)
```
is an `X`.

### The First Commandment of `which-Nat`
If
```
(which-Nat zero
  base
  step)
```
is an `X`, then it is the same `X` as `base`.

### The Second Commandment of `which-Nat`
If
```
(which-Nat (add1 n)
  base
  step)
```
is an `X`, then it is the same `X` as `(step n)`.


The normal form of
```
(which-Nat 5
  0
  (lambda (n)
    (+ 6 n)))
```
is
```
(lambda (n)
  (+ 6 n)
  4)
```
and therefore `10`.

We want to define `gauss`, which is the sum of all numbers <= n. `(gauss 5) = (+ 5 (gauss 4))`. This should be easy to define but we do not allow recursion. The reason is because every expression must have a value. Some recursive definitions make it possible to write expressions that do not have values.

```
(claim forever
  (-> Nat
  Atom))

(define forever
  (lambda (and-ever)
    (forever and-ever)))
```

### Type Values
An expression that is described by a type is a value when it has a constructor at its top. Similarly, an expression that is a type is a value when it has a type constructor at the top.

- `(car (cons Atom 'prune))` is not a type

### Every `U` Is a Type
Every expression described by `U` is a type, but not every type is described by `U`.

Names defined with `define` are neither type constructors nor constructors. Thus, they are not values.

Eliminators allow the information stored within a type to be used.

### Definitions Are Unnecessary
Everything can be done without definitions, but they do improve understanding.

- An expression that exchanges `Nat`s in a pair is `(lambda (a d) (cons d a))`
- An expression that extracts the first `Nat` from a pair is `(lambda (a d) a)`
- The type of `+` is `(-> Nat Nat Nat)`
