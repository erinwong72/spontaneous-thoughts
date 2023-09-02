# GROMACS on Seawulf
1. Edit ~/.bashrc, adding a line 
```bash
source /gpfs/software/gromacs/intel2022.2/intel/epyc/2022.2/bin/GMXRC
```
2. Edit ~/.bash_profile, edit path 
```bash
PATH="/gpfs/software/gromacs/intel2022.2/intel/epyc/2022.2/bin/gmx_mpi:$PATH"
```
3. Load module
```bash
module load gromacs/intel2022.2/mpi/2022.2-epyc
```
 4. To use gromacs, do `gmx_mpi` (basically does same thing as gmx)

To use interactively:

```bash
module load slurm
salloc -N 1 --ntasks-per-node=28 -p short-40core
ssh -X $SLURM_NODELIST
```