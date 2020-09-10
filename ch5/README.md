# Lists, Lists, and More Lists

`List` is a type constructor.

### The Law of `List`
If *E* is a type, then `(List E)` is a type.

- *nil* is a `(List Atom)`
- *nil* is a `(List Nat)`
- *nil* is a `(List (Pair Nat Atom))`
- *nil* is not a `(List 'potato)`

`nil` is a constructor.

The other constructor for a `(list E)` is `::` or *cons*.

`(:: e es)` is a `(List E)` when *es* is a `(List E)`. This includes *nil*. *e* must be an *E* because we can only use an eliminator on the list if we know that everything in the list is an *E*.

### The Law of `nil`
`nil` is a `(List E)` no matter what type *E* is.

### The Law of `::`
If *e* is an *E* and *es* is a `(List E)`,
then `(:: e es)` is a `(List E)`.
