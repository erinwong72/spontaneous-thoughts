# Collision theory for chemical reactions

>[!info] Main idea
>Reactions happen when molecules/particles collides with enough energy > $E_{min}$.

If two molecules don’t collide with enough energy, they simply bounce off each other instead of engaging in the chemical reaction.

The overall equation consists of two parts:
1. **Collision frequency**, based on concentration of molecules, size, speed
	- $$\sigma v_{rel}N_{A}^{2}[A][B]$$
		- $\sigma$ = collision cross-section, the area exposed on a molecule for collision
2. **Activation energy**, dictating that only particles with enough activation energy will lead to reaction
	- The **Boltzmann distribution** is used to calculate the number of molecules that have enough energy
	- $$e^{\frac{-E_{min}}{RT}}$$
		- $E_{min} = E_{a}$
3. **Steric factor** accounts for a preference for a certain relative orientation in the reaction

>[!formula] Collision theory equation
>$$k = A \times e^{\frac{-E_{a}}{RT}}$$
>- $A$: $p \cdot z$, p is steric factor, z is reaction rate → treat A like a constant

Unsimplified form:
$$k = P \times \sigma v_{rel}N_{A}^{2} \times e^{\frac{-E_{a}}{RT}}$$
- Get rate of reaction by multiplying $[A][B]$ back on

This explains [[Temperature effect on reactions]] as well as the nature of *endothermic* vs *exothermic* processes.
- Endothermic has higher activation energy and increased K when T is increased
- Exothermic has lower activation energy and decreased K when T is increased (reverse increases)

---
N
S: [[Temperature effect on reactions]], [[Transition state theory]]
E: [[Harpoon mechanism of reaction]]
W