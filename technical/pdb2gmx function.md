# pdb2gmx function
#technical 

Before converting from PDB to gmx (using pdb2gmx):
- Make sure there are no internal sequences/amino acid residues that are “missing” → will cause pdb2gmx to fail
- Only works for residues defined by force field (proteins, nucleic acids, very few cofactors)

Outputs of pdb2gmx:
1. Molecule topology (.top file)
    1. Defines each moleculetype, first for protein, then for the solvent
    2. Protein
        1. # include ⇒ calls the forcefield parameters
        2. Each residue has it’s own section with the atoms in it, charge, mass, etc.
        3. Dihedrals: angle of rotation around a covalent bond aka torsional angles
        4. Another # include to include the position restraints
    3. Solvent
        1. Different models of even water!
        2. Also # include position-restraint
        3. Ion parameters
    4. System definition = name of system (i.e. lysozyme)
    5. Molecules definition = all molecules in the system, must match exactly the order in the .gro file and the name in the .top file
2. Position restraint (posre.itp) defines force constant that keeps atoms in place during equilibration
3. Post-processed structure file

Common options passed into pdb2gmx:
- -ignh: ignore H atoms, because they must follow the exact naming convention that the force fields in GROMACS expects them to be
- -ter: assign charge states for termini
- -inter: assign charge states for charged residues (Glu, Asp, Lys, Arg, His) and choose which Cys residues are involved in disulfide bonds

Purpose of pdb2gmx: produce a force-field compliant topology
- GROMACS formatted file (.gro) is NOT mandatory, but has all the atoms defined in the force field
- What is a force-field though? [[Force field]]