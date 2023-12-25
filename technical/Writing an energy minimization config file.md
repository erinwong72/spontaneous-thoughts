# Writing an energy minimization config file
Configs will vary based on what force field you use, make sure you're using the right one!
- Download appropriate config from their website (can prob find it through this hub website: [Force fields in GROMACS — GROMACS 2019-rc1 documentation](https://manual.gromacs.org/documentation/2019-rc1/user-guide/force-fields.html))

Must include or else em won't work/converge (defaults listed here usually work):
- integrator = steep
- emtol = 1000.0
- emstep = 0.01
- nsteps = 50000
- The rest is going to be specific to the force field itself