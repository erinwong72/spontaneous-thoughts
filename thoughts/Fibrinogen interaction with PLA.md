# Fibrinogen interaction with PLA
#project

P12 prevents fibrinogen formation → end goal is to develop into a drug to prevent blood clots (implants, etc.)

Fibrinogen:
- Binding to surface releases C domains which causes lateral aggregations
	- But how is it causing the alpha C domains to open up? (on an atomistic level)
- P12 blocks D domain, which is important for locking in the other fibrinogen and forming a soluble fiber
	- Initially only thought it blocked alpha C domain, disallowing lateral aggregation, but need more understanding—in experiments, see that it covers part of the D domain and alpha C domain → here’s where molecular simulations come in
- Where do we come in? How does the whole molecule, but each piece of it, interact with the surface: (break down project to pieces)
	- ![[Pasted image 20230720180014.png]]
	- Matthew: How does D domain interact with hydrophobic surface?
		- Should flatten out , but want to understand computationally
		- But on hydrophilic surface, alpha C mainly interacts
	- Me: E domain should be binding to the hydrophobic surfaces (PLA), but not as strongly as D domain.
		- Get protein from online:
			- 3GHG, want the model with chains A-F (there are two), get rid of the other (using UCSF chimera)
			- Use MatchMaker to align it with one of the models
			- Select the part that has been aligned
			- Remove the other ones you don’t need (should look like this)
				- ![[Pasted image 20230720180058.png]]
		- Take surface
			- Don’t need the whole one, get complementary sheet that will fit each domain
		- Put E domain on top of it, using docking
		- Analysis: Gibbs free energy, residue interactions, compactness
	- Richard: interaction between alpha C domain and E domain
	- Compare energy values from all studies
	- Machine learning classifies when the interactions will occur, mainly learning the coarse-graining

Implant application:
- Coat PLA on P12

Drug application:
- P12 as a drug