# Precisely How Many?

- `nil` has no first entry
- `nil` has no last entry

These observations make it impossible to write a *first* and *last* function for `List`.

Just as some types are the outcome of evaluating an expression, some types contain other expressions that are not themselves types.

- `(Vec Atom 3)` is a type
- *vecnil* is the only constructor for `(Vec E zero)`
- *vec::* is the only constructor for `(Vec E (add1 k))`

### The Law of `Vec`
If *E* is a type and *k* is a `Nat`,
then `(Vec E k)` is a type.

### The Law of `vecnil`
`vecnil` is a `(Vec E zero)`.

### The Law of `vec::`
If *e* is an *E* and *es* is a `(Vec E k)`,
then `(vec:: e es)` is a `(Vec E (add1 k))`.

- `head` is an eliminator for `Vec`
- `(head es)` is an *E* when *es* is a `(Vec E (add1 k))`
- `tail` is an eliminator for `Vec`
- `(head es)` is an `(Vec E k)` when *es* is a `(Vec E (add1 k))`

### The Law of `Pi`
The expression `(Pi ((y Y)) X)` is a type when *Y* is a type, and *X* is a type when *y* is a *Y*.

### Use a More Specific Type
Make a function total by using a more specific type to rule out unwanted arguments.

For a given `Nat` *l*, the value can be any number including zero. A `Vec` of length *l* can be empty if *l* is zero. A `Vec` of length `(add1 l)` is always at least one. Using this in type definitions rules out empty vectors which cannot use the eliminators we describe above.

### -> and Pi
The type `(-> Y X)` is a shorter way of writing `(Pi ((y Y)) X)` when *y* is not used in *X*.

### The Final Law of lambda
If *x* is an *X* when *y* is a *Y*,
then `(lambda (y) x)` is a `(Pi ((y Y)) X)`.

### The Final Law of Application
If *f* is a `(Pi ((y Y)) X)` and *z* is a *Y*,
then `(f z)` is an *X* where every *y* has been consistently replaced by *z*.

### The Final First Commandment of lambda
If two lambda-expressions can be made the same `(Pi ((y Y)) X)` by consistently renaming their variables,
then they are the same.

### The Final Second Commandment of lambda
If *f* is a `(Pi ((y Y)) X)` and *y* does not occur in *f*,
then *f* is the same as `(lambda (y) (f y))`.
