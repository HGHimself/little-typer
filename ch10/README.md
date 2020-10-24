# It Also Depends on the List

We have learned about vectors and lists. Vectors have a defined length while lists do not. Can you append a list onto a vector? Sure! But we cannot use `append`; instead we must use `vec-append`.

A value is a `(Pair A D)` if
1. it has `cons` at the top,
1. its `car` is an *A*, and
1. its *cdr* is a *D*.

If `(cons a d)` is a `(Sigma ((x A)) D)`,
then *a*'s type is *A* and *d*'s type is found by consistently replacing every *x* in *D* with *a*.

The expression `(Sigma ((x A)) D)` is a type when
1. *A* is a type, and
1. *D* is a type if *x* is an *A*.

- `(Sigma ((bread Atom)) (= Atom bread 'bagel))` is a type when *bread* is an Atom.
- `(cons 'bagel (same 'bagel))` has the type of above.
- `(Sigma ((A U)) A)` is a type.
- `(cons Nat 4)` has the above type.
- `(cons Atom 'bagel)` has the above type.
- `(cons (= Nat zero zero) (same zero))` has the above type.

### The Law of Sigma
The expression `(Sigma ((x A)) D)` is a type when *A* is a type, and *D* is a type if *x* is an *A*.

### The Commandment of `cons`
If *p* is a `(Sigma ((x A)) D)`,
then *p* is the same as `(cons (car p) (cdr p))`

The relationship between `Pair` and `Sigma` is `(Pair A D)` is a short way of writing `(Sigma ((x A)) D)` where *x* is not used in *D*. This is similar to how some Pi-expressions can be written as ->-expressions.

We can use Sigma to combine a number of entries with a vector like so:
`(Sigma ((l Nat)) (Vec Atom l))`

This is awesome, because now we can package the vector and its length into one neat type.

A `(Pair A D)` consists of both evidence for *A* and evidence for *D*, with `cons` at the top. This means that `(Pair A D)` can be read "*A* and *D*" because to give evidence for an "and" is to give evidence for both parts.

`(Pair (= Nat 2 3) (= Atom 'apple 'apple))` can be read as "2 equals 3 and 'apple  equals 'apple." We cannot provide evidence for this because 2 does not equal 3 so we cannot put anything in the *car*.

Evidence for `(Sigma ((x A)) D)` is a pair whose *car* is an *A* and whose *cdr* is evidence for the statement found by consistently replacing each *x* in *D* with the *car*.

A Sigma-expression can be read as "there exists." Here are some examples:
```
(Sigma ((es (List Atom)))
  (= (List Atom)
    es
    (reverse Atom es)))
```
"There exists a list of atoms that is equal to itself reversed." This is true for any palindrome.

```
(Sigma ((es (List Atom)))
  (= (List Atom)
    (snoc Atom es 'grape)
    (:: 'grape es)))
```
"There exists a list of atoms where adding 'grape to the end of the list or the front of the list does the same thing." This is true for any list that has 'grape only for its members.

### The Law of `ind-List`
If *target* is a `(List E)`, *mot* is an `(-> (List E) U)`, *base* is a `(mot nil)`, and *step* is a `(Pi ((e E) (es (List E)) (-> (mot es) (mot (:: e es)))))`,
then `(int-List target mot base step)` is a `(mot target)`.

### The First Commandment of `ind-List`
The ind-List-expression `(int-List nil mot base step)` is the same `(mot nil)` as *base*.

### The Second Commandment of `ind-List`
The ind-List-expression `(int-List (:: e es) mot base step)` is the same `(mot (:: e es))` as `(step e es (int-List es mot base step))`.
