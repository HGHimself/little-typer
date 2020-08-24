# The More Things Change, the More They Stay the Same

### The Law of Tick Marks
A tick mark directly followed by one or more letters and hyphens is an `Atom`.

- 'Atom
- 'coeurs-d-artichauts
- 'ratatouille

### The Commandment of Tick Marks
Two expressions are the same `Atom` if their values are tick marks followed by identical letters and hyphens.

### The Law of `Atom`
`Atom` is a type.

A **judgement** is an attitude that a person takes towards expressions. When we come to know something, we are making a judgement.

### The Four Forms of Judgement
1. _ is a _
2. _ is the same _ as _
3. _ is a type
4. _ and _ are the same type

Judgements are acts of knowing, and believing is part of knowing.

To ask whether an expression is described by a type, one must have already judged that the supposed type is a type.

To ask whether two expressions are the same according to a type, one must first judge that both expressions are described by the same type.

In order to judge that both aforementioned expressions are the same type, one must first judge that each expression is, in fact, a type.

- Is `(car (cons 'ratatouille 'baguette))` the same `Atom` as 'ratatouille?
- Is `(cdr (cons 'ratatouille 'baguette))` the same `Atom` as 'baguette?

The **normal form** of an expression is the most direct way of writing it.

Any two expressions that are the same have identical normal forms, and any two expressions with identical normal forms are the same.

### Normal Forms
Given a type, every expression described by that type has a *normal form*, which is the most direct way of writing it. If two expressions are the same, then they have identical normal forms, and if they have identical normal forms, then they are the same.

### Normal Forms and Types
Sameness is always according to a type (see Form of Judgement 2), so normal forms are also determined by a type.

- The normal form of the `(Pair Atom Atom)` `(car (cons (cons 'aubergine 'courgette) 'tomato))` is `(cons 'aubergine 'courgette)`.

To be a `(Pair Atom Atom)`, one must be a pair whose `car` is an `Atom`, and whose `cdr` is an `Atom`, or an expression that is the same as such pair.

### The First Commandment of `cons`
Two `cons`-expressions are the same `(Pair A D)` if their `car`s are the same `A` and their `cdr`s are the same `D`. Here, `A` and `D` stand for any type.

### Normal Forms of Types
Every expression that is a type has a normal form, which is the most direct way of writing that type. If two expressions are the same type, then they have identical normal forms, and if two types have identical normal forms, then they are the same type.

- `(Pair (car (cons Atom 'olive)) (cdr (cons 'oil Atom)))` and `(Pair Atom Atom)` are the same type.

`Pair` uses types to construct a new type. `Pair` does not accept *an* `Atom` for its `cdr` or `car`. `Pair` **does** accept `Atom` for its `cdr` or `car`.

- `Nat` is a type
- 1729 is a `Nat`
- 0 is a `Nat`
- -1 is not a `Nat`
- -42 is not a `Nat`

We can get all `Nat`s by using `add1`.
- `zero`
- `(add1 zero)`
- `(add1 (add1 zero))`
- `(add1 (add1 (add1 zero)))`
- `(add1 (add1 (add1 (add1 zero))))`

**Important Observation:** If `n` is a `Nat`, then `(add1 n)` is always positive, even if `n` is 0.

### Claims before Definitions
Using define to associate a name with an expression requires that the expression's type has previously been associated with the name using `claim`.

To be normal is to have a constructor at the top of the expression, and the value under this constructor is also normal.

`add1` is a constructor. It can be said that `(add1 n)` *constructs* a new `Nat` that is 1 bigger than the original `Nat` n.

If we define `8` as follows:
```
(add1
  (add1
    (add1
      (add1
        (add1
          (add1
            (add1
              (add1 zero))))))))
```
We can see that 8 is normal, since its top is `add1`.

The value underneath, namely `7`, is also normal due to the `add1` at the top.

From either of these facts, we can deduce that `zero` is also normal, otherwise neither `8` nor `7` would be normal.

### Values
An expression with a constructor at the top is called a *value*

- `(add1 (+ (add1 zero) (add1 (add1 zero))))` is not normal
- `(add1 (+ (add1 zero) (add1 (add1 zero))))` is a value

Not all values are normal, but all normal expressions are values.

A constructor expression is a direct way of building expressions with the new type.

### Values and Normal Forms
Not every value is in normal form. This is because the arguments to a constructor need not be normal, Each expression has only one normal form, but it is sometimes possible to write is as a value in more than one way.

- `(add1 'aubergine)` is not a value

Finding a value is the same as some starting expression is called *evaluation*.

In this context, there is nothing but expressions and what we judge about them.

A normal expression has no remaining opportunities for evaluation. Usually, expressions that are normal are easier to understand. Finding a value is often enough, however, because the top constructor can be used to determine what must happen next.

- `(add1 (+ (add1 zero) (add1 (add1 zero))))` is the same `Nat` as `four`

Two `Nat` expressions, that aren't values, are the same if their values are the same. There are exactly two ways in which two `Nat` values can be the same: one for each constructor.

### The Commandment of `zero`
`zero` is the same `Nat` as `zero`.

### The Commandment of `add1`
If `n` is the same `Nat` as `k`, then `(add1 n)` is the same `Nat` as `(add1 k)`.

To find the value of a `car`-expression, start by finding the value of its argument.

- `cons` is a constructor for `Pair`
- All atoms, like `'bay` and `'leaf` are contsructors for `Atom`
