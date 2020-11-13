# Imagine That...

We have proved many expressions are equal. We know that not all expressions are equal though.

39 is not equal to 117.

We can write this as a type: `(-> (= Nat 39 117) Absurd)`. We can use the form `(-> X Absurd)` to mean "not *X*". It says if there were a proof that 39 equals 117, then there would be a proof of Absurd. We know no such proof exists.

How can a "not" statement have a proof if there are no Absurd values? The key is to carefully avoid having to write the body of the lambda-expression. We can do this is `=consequence`.

If `zero` equals `zero`, nothing interesting is learned, and we can represent this with a `Trivial`.

To better understand `Trivial`, you must understand that it has no eliminator, and there is only one `Trivial` value. There is nothing to be learned from eliminating it, and is a boring statement that can always be proved.

If `(= Nat (add1 n-1) zero)` or `(= Nat (add1 j-1) zero)` are true, then anything at all can be true. So the consequence is `Absurd`.

If `(= Nat (add1 n-1) (add1 j-1))` is true, then *n-1* and *j-1* are the same `Nat`.

### Imagine That...
Using types, it is possible to *assume* things that may or may not be true, and then see what can be concluded from these assumptions.

The type `(-> (= Nat 0 6) (= Atom 'powdered 'glazed))` can be read as "If zero equals six, then powdered donuts are glazed donuts." Because there is not evidence for "zero equals six", there are no suitable arguments for this function.

Sameness is not a type, it is a judgement. Either two expressions are the same or they are not the same, but there is no way to provide evidence of this sameness. Types, such as =-expressions, *can* have evidence.

More things are equal then are the same. The fact that any two expressions either are or are not the same means that we are freed from the obligation to provide proof because sameness can be determined by following the Laws and Commandments.

Equality requires *proof* and therefor is more expressive. Recognizing a proof requires only the Laws and Commandments, but constructing a proof may require creativity, ingenuity, and hard work.

### Sameness versus Equality
Either two expressions are the same, or they are not. It is impossible to prove that they are the same because sameness is a judgement, not a type, and a proof is an expression with a specific type.
