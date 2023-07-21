# Ellipsoid Interactions with Potentials
#project 

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