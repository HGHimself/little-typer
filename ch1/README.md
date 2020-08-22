# The More Things Change, the More They Stay the Same

#### The Law of Tick Marks
A tick mark directly followed by one or more letters and hyphens is an `Atom`.

- 'Atom
- 'coeurs-d-artichauts
- 'ratatouille

#### The Commandment of Tick Marks
Two expressions are the same `Atom` if their values are tock marks followed by identical letters and hyphens.

#### The Law of `Atom`
`Atom` is a type.

A **judgement** is an attitude that a person takes towards expressions. When we come to know something, we are making a judgement.

#### The Four Forms of Judgement
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

#### Normal Forms
Given a type, every expression described by that type has a *normal form*, which is the most direct way of writing it. If two expressions are the same, then they have identical normal forms, and if they have identical normal forms, then they are the same.

#### Normal Forms and Types
Sameness is always according to a type (see Form of Judgement 2), so normal forms are also determined by a type.

- The normal form of the `(Pair Atom Atom)` `(car (cons (cons 'aubergine 'courgette) 'tomato))` is `(cons 'aubergine 'courgette)`.

To be a `(Pair Atom Atom)`, one must be a pair whose `car` is an `Atom`, and whose `cdr` is an `Atom`, or an expression that is the same as such pair.

#### The First Commandment of `cons`
Two `cons`-expressions are the same `(Pair A D)` if their `car`s are the same `A` and their `cdr`s are the same `D`. Here, `A` and `D` stand for any type.

#### Normal Forms of Types
Every expression that is a type has a normal form, which is the most direct way of writing that type. If two expressions are the same type, then they have identical normal forms, and if two types have identical normal forms, then they are the same type.

- `(Pair (car (cons Atom 'olive)) (cdr (cons 'oil Atom)))` and `(Pair Atom Atom)` are the same type.

`Pair` uses types to construct a new type. `Pair` does not accept *an* `Atom` for its `cdr` or `car`. `Pair` **does** accept `Atom` for its `cdr` or `car`.

- `Nat` is a type
- 1729 is a `Nat`
- 0 is a `Nat`
- -1 is not a `Nat`
- -42 is not a `Nat`

We can get all `Nat`s by using `add1`.

**Important Observation:** If `n` is a `Nat`, then `(add1 n)` is always positive, even if `n` is 0. 
