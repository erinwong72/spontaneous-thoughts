# Fixing missing atoms or residues in PDB structures
Two ways:
1. PyMol
2. Modeller
## PyMol Way
Based on this wonderful tutorial: [Building missing residues in PDB structure as loop regions using PyMol](https://www.youtube.com/watch?v=b_zyj7mm3pM&t=12s)

1. In the PyMol “command line”, type `fetch protein_name` where protein_name is the name of your protein
2. Select: Display → Sequence (to show the missing residues, which will be *gray*)
3. Remove water atoms by selecting them (the 0s) with your mouse on the sequence panel and typing in the following lines:

```python
select sel
remove sel
```

4. Select the first residue and last residue, which will be grouped in the **(sele)** class on the right.
	1. Select S on the (sele) row and show as “Licorice”
	2. Select C in the same area and choose color by element (3rd choice) 
	- ![[Pasted image 20230826114616.png|317]]
5. Click on “Builder” and navigate to the Protein tab once a window pops up
	1. Choose secondary structure to be **Beta Sheet (Antiparallel)**
	2. Select the **nitrogen** of the first residue (which will be in blue if you color-coded by element properly) (N-terminus)
	3. Go to the builder panel and select the appropriate next amino acid residue (refer to the gray letter codes in the sequence)
	4. Once that residue has been appended, the tool will automatically select the next nitrogen for you
	5. Repeat the same process until you finished filling in the missing residues for the N-terminus
	6. It’ll look a little funny, but go to **(sele)** again and show as licorice like before → now it should look better
	7. Do the same for the C-terminus, except build from the **carbon** of the last existing residue—it will again automatically select the carbon for the next residue

>[!tip]
> If you don’t see a nitrogen/carbon for the last residue, delete that residue and build from the *second-to-last* residue.
> 
> Ex. The last residue is D: delete it, set the previous residue to show as licorice, select the nitrogen, and click Asp in the builder (since it corresponds to D). Then continue as you would, building the missing residues.

6. Save the reconstructed molecule by selecting File → Export Molecule:
	- Don’t change anything under **Generic Options**
	- Make sure the following is all selected in **PDB Options**
		- Write segment identifier column
		- Retain atom ids
		- Write HEADER for every object

7. Refine loop regions (make them energetically favorable) using modeller’s [ModLoop](https://modbase.compbio.ucsf.edu/modloop/)
	- Modeller license key is universal: ==MODELIRANJE==
	1. Upload the modified pdb file
	2. The loop segments should be denoted in the following format: `starting_loop_residue_number:chain_letter:ending_loop_residue_number:chain_letter:`
		- If there is a break in the loop (like you have two segments or more), press enter and do the same on a new line for the second loop.
		- One loop segment representation would look like this: `1:A:4:A:`, so the loop spans residues 1 to 4 on chain A (including residue 4)
	- Once you click submit, you should see instructions on how to get results and such
		- Download the pdb file from the results page