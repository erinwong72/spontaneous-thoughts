# Lysozyme in Water GROMACS
#technical 

## 1. Prepare topology

1. Remove the waters
2. [[pb2gmx function]]

## 2. Defining unit cell and adding solvent

1. Define dimensions of box using editconf (genbox)
	1. Choosing a unit cell: recommended is *rhombic dodecahedron* b/c volume is less than regular cubic box so less solvent is needed (save on simulation time)
	2. Specific args:
		1. -c: centers protein
		2. -d: distance from edge (minimum)
			1. Needs to be set correctly so that the [[Minimum image convention]] can be set for [[Periodic boundary conditions]]
			2. The protein cannot overlap with its periodic images (cannot directly interact)
		3. -bt: box type
2. Fill box with solvent using solvate module
	1. Specific args:
		1. -cp: configuration of the protein (.gro file)
		2. -cs: configuration of the solvent (already in GROMACS)
		3. -p: name of the topology file that can be modified with the appropriate “solvated” info
			1. Keeps track of number of water molecules added which will be seen in topology, but this is ONLY for water solvents

## 3. Adding ions

Because the protein is charged after solvation, ions must be added to neutralize the solution.

Use genion: adds the ions
- Replaces specific water molecules in the topology with specified ions
- Input: .tpr file, created using GROMACS pre-processor ([[grompp module]])
- Specific args:
	- -s: state file (.tpr file)
	- -p: process topology file
	- -pname, -nname: positive and negative ion names
	- -neutral: make the net charge neutral
	- -conc: specific concentration of ions
- Choose 13 to select replace *solvent* with ions
- Genion will add to the moleculetype section of the topology the name of the ion(s) added

## 4. Energy Minimization

Energy minimization = relaxation of structure, making sure nothing about the geometry is impossible.

- Very similar to adding ions, also uses [[grompp module]]
- Use mdrun, the molecular dynamics engine (on the .tpr file)
	- Special args:
		- -v: verbose
		- -deffnm: defines file names of input and output
			- If input isn’t em.tpr, specify using -s
- Output:
	- em.log
	- em.edr: energy file, contains all energies collected through the minimization
	- em.trr
	- em.gro
	- WATCH OUT! Make sure:
		- Potential energy should be negative
		- Max force should be less than the target set in the .mdp file

## 5. Equilibration

Equilibration needs to be done so that the solvent is optimized for the solute as well, and so the system doesn’t collapse when the dynamics is done. Involves two properties to be optimized:
1. Temperature
2. Density

Use posre.itp file (position restraint) from first step here:
- Apply position **restraining force** on all atoms of the protein except for hydrogen, so solvent can be equilibrated without messing up too much of the protein’s structure
	- Can move, but heavily penalized

Two phases of equilibration:
1. NVT ensemble (constant Number of particles, Volume, Temperature) or “isothermal-isochoric” = **temperature** stabilization
	1. When reached optimal temperature, it will plateau
	2. Same steps as energy minimization step and ion adding (generate .tpr file via grompp, use mdrun)
		1. .mdp file (which has params): important ones
			1. gen_vel (velocity generation) allows for multiple simulations to be created from the same structure using different initial velocities
			2. tcoupl=V-rescale: [[Velocity rescaling thermostat]]
			3. pcoupl, no pressure coupling applied
	3. Takes quite a long time
2. NPT ensemble (constant Number of particles, Pressure, and Temperature) or “isothermal-isobaric” = *pressure* stabilization
	1. .mdp important params:
		1. continuation=yes, because continuing from NVT phase
		2. gen_vel=no, use velocities from the trajectory
		3. pcouple, use [[Parrinello-Rahman barostat]]
	2. When checking pressure, don't be too alarmed by the fluctuations, it is supposed to/generally fluctuates a lot throughout simulations