# Ellipsoid Interactions with Potentials
#project 

## Description

Find a way to use data and all atom simulations to learn a potential for ellipsoid interactions, like the Oliver Diamond one.
- Feed position and orientation of ellipsoids and get a number = potential between the two, compare to ground truth
- Trying a regular feed forward neural net → loss doesn’t go all the way to zero, bounces a bit
- Trying to fit data to some function in the form of those in the papers → physics informed
	- Trying to find params and coefficients that give the values (instead of it being a black box)

Refer to Giorgos’ presentation:
- PINN uses neural network (black box) to tune the whole x12n12 quantity instead of the individual params, and then from the whole expression, a few others — doesn’t seem like a very physics-informed neural network
	- ![[Pasted image 20230720180236.png]]
- Add multi-layer perceptron layers to balance meaningful loss with some arbitrary loss?
- Does changing the number of particles in the ellipsoid alter the ground truth significantly
	- Should not change it bc averages out
		- Create big dataframe
- Make sure ground truth training is correct and valid

## Literature

[[(2016) Systematic Generation of Anisotropic Coarse-Grained Lennard-Jones Potentials and Their Application to Ordered Soft Matter.pdf]]
- Created model for ellipsoid potentials using a coarse-grained representation at various levels of detail by comparing/running an all-atom force field for each ellipsoid
- Control level of detail (LoD) by designating how many ellipsoids to use (i.e. one ellipsoid for every atom or one ellipsoid for the whole molecule)