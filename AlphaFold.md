# AlphaFold

[[s41586-021-03819-2.pdf|Highly Accurate Protein Structure Prediction with AlphaFold (paper)]]

## Background
Two methods in predicting 3D structures from protein sequence:
1. Physical interactions (aka function)
	- Involving simulations (physics and statistics)
	- But (cons):
		1. Computationally expensive, no known efficient way to do this
		2. May depend on context
		3. Physics of proteins is lacking
2. Evolutionary history
	- Using close homologs to predict structure
	- Pro:
		- **Protein Data Bank**
		- Lots of data from the explosion of sequencing
	- Cons:
		1. Not very experimentally accurate
			- Especially when there are no known folded structures for close homologs (it hasn't been "solved")

Lead to a need for a computational approach that can predict protein structures accurately (close to experimental accuracy is desired). Enter **AlphaFold**(v2), a neural network.

## Results
(The paper presents results first???)

Based on CASP14, a global assessment used to "test" algorithms in the protein-folding space, using blind or recently solved structures. CASP14 was held in 2020.

AlphaFold predictions were accurate (using [[Root mean square deviation]]) down to around the size of a carbon atom, when comparing all atoms (median of 1.5 angstroms vs 1.4 angstroms). They were also much more accurate than the previous best method (3.5 angstroms). For the backbone atoms, the median was 0.96 angstroms, compared to the previous best of 2.8 angstroms. The model still retains this accuracy even as the proteins predicted on become larger and longer, accounting for domain packing (simply that hydrophobic domains will be pushed towards the center and hydrophilic ones less so).

The model continued to perform well on novel Protein Data Bank structures (not seen by the model). 
- The confidence measure (predicted [[Local Distance Difference Test]] was able to serve as a reliable proxy of the actual accuracy of the prediction itself.
- [[Template Modeling score]] was similarly also accurately predicted

So, what the model is telling you is likely what is happening :D.