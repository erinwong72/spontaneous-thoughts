# grompp module
#technical

aka GROMACS pre-processor

Creates .tpr file, commonly used for simulation and neutralizing by adding ions.

Inputs:
- Topology + coordinate file (.gro file) + .mdp (molecular dynamics generator file)
- .mdp usually used for energy minimization or molecular dynamics
    - Can literally be any legit combination of parameters
    - Easier to use energy-minimization script

Specific args:
- -f: .mdp file
- -c: .gro file
- -p: topology file