# Pick a Number, Any Number

- The normal form of `(+ 1)` is `(lambda (j) (add1 j))`
- `incr` will add1 to its taget *n*
- The relationship between `incr` and `(+ 1)` is they both find the same answer, no matter what the argument is

Does this mean that `(+ 1)` is the same `(-> Nat Nat)` as `incr`?

They are the same if they have the same normal form.
- The normal form of `(+ 1)` is `(lambda (j) (add1 j))`
- The normal form of `incr` is `(lambda (n) (iter-Nat n 1 (lambda (j) (add1 j))))`
- They are not the same `(-> Nat Nat)`

Even though they are not the same, the fact that they always find the same answer can be written as a type.

Sameness is a judgement, not a type. But with a new type constructor, types can express a new idea called *equality*.

### The Law of =
An expression
`(= X from to)`
is a type if *X* is a type, *from* is an *X*, and *to* is an *X*.

*NOTE:* `=` is another way to construct a dependent type, since *from* and *to* need not be types.

### Reading FROM and TO as Nouns
Because *from* and *to* are convenient names, the corresponding parts of an =-expression are referred to as the FROM and TO.

- `(= Atom 'kale 'blackberries)` is a type
- `(= Nat (+ 1 1) 2)` is a type
- `(= (car (cons Nat 'kale)) 17 (+ 14 7))` is a type
- `(= (car (cons Nat 'kale)) 15 (+ 14 7))` is a type, even if the Nats are not equal

*IMPORTANT:* Types can be read as statements.

- `(= Atom 'apple 'apple)` can be read: "The expressions `'apple` and `'apple` are equal `Atoms`."
- `(= Nat (+ 2 2) 4)` can be read: "Two plus two equals four."

- "Three plus four equals seven" is another way of writing the type `(= Nat (+ 3 4) 7)`
- `(+ 3 4)` is the same `Nat` as `7` is a **judgement**
- "Three plus four equals seven is a type" is a judgement

A judgement is not an expression- rather, a judgement is an attitude that a person takes when thinking about expressions.

We had previously said that a judgement is knowing and believing is part of knowing. Interpret this how you please :)

A Pi-expression can be read as "for every."
```
(Pi ((n Nat))
  (= Nat (+ 1 n) (add1 n)))
```
can be read as "For every Nat *n*, `(+ 1 n)` equals `(add1 n)`."

If a type can be read as a statement, then judging the statement to be true means that there is an expression with that type. Saying that "`(+ n 0)` and *n* are equal Nats." means "There is an expression with type `(= Nat (+ n 0) n)`."

If there exists an expression of a given type, then we have a *proof* the type is true.

#### How can a Nat be proved?
Pick a number. 15? Good job, you have a proof.

Another way to think about statements is an expectation of a proof, or as a problem to be solved. Think of a `claim`, which then expects a definition.

Here, a proofs are values, and values are expressions with constructors at their top.

### The Law of same
The expression `(same e)` is an `(= X e e)` if e is an *X*.

- The expression `(same 21)` is an `(= Nat (+ 17 4) (+ 11 10))`
- The expression `(same (incr 3))` is an `(= Nat (+ 2 2) 4)`

Now we can write expressions that originally could only be judged. The important part of this is that expressions can be used together with other expressions. By combining Pi and =, we can write statements that are true for arbitrary Nats.

### The Law of cong
If *f* is an `(-> X Y)` and *target* is an `(= X from to)`,
then `(cong target f)` is an `(= Y (f from) (f to))`.

### The Commandment of cong
If *x* is an *X*, nad *f* is an `(-> X Y)`,
then `(cong (same X) f)` is the same `(= Y (f x) (f x))` as `(same (f x))`.
