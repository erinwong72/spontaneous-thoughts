# How to use mpi4py (parallel processing) on HPC
For Seawulf, but I would imagine that it would also work for other HPC servers.

1. Request an interactive job using srun:
```bash
module load slurm
srun -J gt_generation -N 1 -p extended-96core --ntasks-per-node=20 --pty bash
```

2. 