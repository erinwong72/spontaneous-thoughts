# Writing an equilibration config file
The ultimate guide (if you can bear to read through it): [Molecular dynamics parameters (.mdp options) - GROMACS 2023.2 documentation](https://manual.gromacs.org/current/user-guide/mdp-options.html)

While you're writing it, make sure to reference the one from the website!

Temperature (NVT):
- tau-t = time constant for coupling, set one for each group
- ref-t = reference temperature for coupling, also one for each group
- tc-groups = groups to separately couple, make sure they're defined in the topol.top file (protein, non-protein should be a good starting point)

Pressure (NPT):
-  continuation = yes → want to continue from NVT
- gen_vel = no → want to read velocities from the trajectory
- pcoupl = Parrinello-Rahman (can choose any)
- pcoupltype = isotropic
- compressibility = depends on isothermal compressibility of solvent
- refcoord_scaling = com (center of mass)
- KEEP TEMP COUPLING ON!

```C++
define = -DPOSRES
; Run parameters
integrator = md
dt = 0.002
nsteps = 50000
nstcomm = 100

; Output control
nstxout = 0
nstvout = 0
nstenergy = 0
nstlog = 0

; Bond parameters
continuation = no
constraint_algorithm = lincs
constraints = h-bonds
lincs_iter = 1
lincs_order = 4

; Neighborsearching
ns_type = grid
nstlist = 10
rlist = 1.2
rcoulomb = 1.2
rvdw = 1.2
rvdw-switch = 1.0
rlistlong = 1.4

; Electrostatics
coulombtype = PME
pme_order = 4
fourierspacing = 0.16

; Relative dielectric constant
epsilon_r = 1
epsilon_rf = 1

; Temperature coupling
tcoupl = V-rescale
tc-grps = protein non-protein
tau_t = 0.1 0.1
ref_t = 300 300

; Pressure coupling
pcoupl = no

; Periodic boundary conditions
pbc = xyz

; Dispersion correction
DispCorr = no

; Van der Waals
vdwtype = cutoff
vdw-modifier = force-switch

; Velocity generation
gen_vel = yes
gen_temp = 300
gen_seed = -1
cutoff-scheme = Verlet
```