# Even Haf a Baker's Dozen

We can say that every natural number is either even or odd. We can prove this with a new type, `Either`.

### The Law of Either
`(Either L R)` is a type if *L* is a type, and *R* is a type.

There are two constructors. If *lt* is an *L*, then `(left lt)` is an `(Either L R)`. If *rt* is an *R*, then `(right rt)` is an `(Either L R)`. Two `(Either L R)` values are the same when their left values are the same *L* and their right values are the same *R*.

### The Law of `left`
`(left lt)` is an `(Either L R)` if *lt* is an *L*.

### The Law of `right`
`(right rt)` is an `(Either L R)` if *rt* is an *R*.

The eliminator for *Either* is called `ind-Either`. It has two bases but no step. It is not recursive because the two constructors, *left* and *right* are not recursive. The motive explains, like usual, why the target is being eliminated.

### The Law of `ind-Either`
If *target* is an `(Either L R)`, *mot* is an `(-> (Either L R) U)`, *base-left* is a `(Pi ((x L)) (mot (left x)))`, and *base-right* is a `(Pi ((x R)) (mot (right x)))`,
then `(ind-Either target mot base-left base-right)` is a `(mot target)`.

### The First Commandment of `ind-Either`
`(ind-Either (left x) mot base-left base-right)` is the same `(mot (left x))` as `(base-left x)`.

### The Second Commandment of `ind-Either`
`(ind-Either (right x) mot base-left base-right)` is the same `(mot (right x))` as `(base-right x)`.
