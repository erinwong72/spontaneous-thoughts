# Molecular dynamics run (MDrun) analysis

1. Center the protein and account for periodicity ([[Periodic boundary conditions]])

```bash
gmx_mpi trjconv -f md.xtc -s md.tpr -o md_noPBC.xtc -pbc mol -ur compact -center
```
- Choose 1 (protein) then 0 (system)

2. Use rms function to get a nice plot of the RMSD, which should be less than 1, somewhere around 0.1

```bash
gmx_mpi rms -s md.tpr -f md_noPBC.xtc -o rmsd.xvg -tu ns
```
- ns for it to be in nanoseconds
- Chose 4 both times to do it on the backbone