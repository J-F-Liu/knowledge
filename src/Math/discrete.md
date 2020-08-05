# Discrete Mathematics

## Mathematical Statements

A statement is any declarative sentence which is either true or false.

A statement is atomic if it cannot be divided into smaller statements, otherwise it is called molecular.

You can build more complicated (molecular) statements out of simpler (atomic or molecular) ones using logical connectives.

#### 5 Logical Connectives:

- P ∧ Q is read “P and Q,” and called a conjunction.
- P ∨ Q is read “P or Q,” and called a disjunction.
- P → Q is read “if P then Q,” and called an implication or conditional.
- P ↔ Q is read “P if and only if Q,” and called a biconditional.
- ¬P is read “not P,” and called a negation.

Truth Conditions for Connectives.
- P ∧ Q is true when both P and Q are true
- P ∨ Q is true when P or Q or both are true.
- P → Q is true when P is false or Q is true or both.
- P ↔ Q is true when P and Q are both true, or both false.
- ¬P is true when P is false.

Conditional has a slightly different meaning in mathematics than it does in ordinary usage, the only way for P → Q to be false is for P to be true and Q to be false.

A sentence that contains variables is called a predicate. To turn it inot a statement, we need to quantify the variable.

##### Universal and Existential Quantifiers.

The existential quantifier is ∃ and is read “there exists” or “there is.” For example, ∃x(x < 0) asserts that there is a number less than 0.

The universal quantifier is ∀ and is read “for all” or “every.” For example, ∀x(x ≥ 0) asserts that every number is greater than or equal to 0.

Quantifiers and Negation.
```
 ¬∀xP(x) is equivalent to ∃x¬P(x).
 ¬∃xP(x) is equivalent to ∀x¬P(x).
```