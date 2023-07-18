# Local Distance Difference Test
aka LDDT

Another way of quantifying protein structure similarity, but not just using superposition like most other similarity scores do.

**Why?** In large proteins with many domains, superposition scores don't account for the fact that they may be in different orientations, so individual domains have to be compared. But then this leads to the fact that comparison of such individual domains means relying on the accuracy of non alpha carbons, which actually make up most of the molecule, so probably not the best method.

**How?** It compares inter-atomic distances instead! So everything is relative and no processing needs to be done when comparing multi-domain structures.