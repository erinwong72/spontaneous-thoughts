# Gyration tensor

2nd order tensor that describes the moment(s) of inertia of a system in all 3 dimensions.

Basically the moment of inertia formula for a rigid body, but with some modifications/additional terms.

For a system of particles, the gyration tensor is defined as:

$G_{ij} = Σ m_i * (r{_i^2} * δ_{ij} - ri_i * ri_j)$

where:
- $G_{ij}$ is the element of the gyration tensor.
- $mi$ is the mass of the ith particle.
- $ri$ is the position vector of the ith particle with respect to the center of mass.
- $δ_{ij}$ is the Kronecker delta, which is equal to 1 if i = j and 0 otherwise.