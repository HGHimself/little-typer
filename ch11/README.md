# All Lists Are Created Equal

Sometimes types are dependent on a number, which is when we use `ind-Nat`. Other times types are dependent on a vector, so we use `ind-Vec`.

### The Law of `ind-Vec`
If *n* is a `Nat`,
*target* is a `(Vec E n)`,
*mot* is a `(Pi ((k Nat)) (-> (Vec E k) U))`,
*base* is a `(mot zero vecnil)`,
and *step* is a `(Pi ((k Nat) (h E) (t (Vec E k))) (-> (mot k t) (mot (add1 k) (vec:: h t))))`,
then `(ind-Vec n target mot base step)` is a `(mot n target)`.

### The First Commandment of `ind-Vec`
The ind-Vec-expression `(ind-Vec zero vecnil mot base step)` is the same `(mot zero vecnil)` as *base*.

### The Second Commandment ofd `ind-Vec`
The ind-Vec-expression `(ind-Vec (add1 n) (vec:: e es) mot base step)` is the same `(mot (add1 n) (vec:: e es))` as `(step n e es (ind-Vec n es mot base step))`.
