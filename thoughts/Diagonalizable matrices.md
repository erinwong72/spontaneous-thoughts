# Diagonalizable matrices

$A \sim D$, which is a diagonal matrix, so A is diagonalizable.

Based on:
- A and D have the same eigenvalues
- If D is diagonal, the diagonal values are eigenvalues

## Criterion for diagonalizability

>[!important] Theorem
If A has an eigenbasis, then A is diagonalizable and vice versa.
- If all the eigenvalues are **distinct**, then there exists an eigenbasis
	- $dim(S_{\lambda})$ = 1 for all $\lambda$ → sum = n → thus there exists enough terms to make it a basis

What about with repeated eigenvalues, does an eigenbasis still exist?
Yes, if some multiplicity “makes up” for the absence of an eigenvalue:
- Algebraic multiplicity = geometric multiplicity
	- So only have to check for eigenvalues with algebraic multiplicity **> 1** (auto equal if multiplicity = 1).
- Repeated # of $\lambda$ = $\sum dim(S_{\lambda})$
	- But what is the [[Dimension of an eigenspace]]?

---
N
S
E
W