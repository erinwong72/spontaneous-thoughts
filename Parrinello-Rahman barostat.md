# Parrinello-Rahman barostat

Similar to the [[Velocity rescaling thermostat]], this maintains the target pressure in a system. It essentially couples the system to an external pressure bath which alters the volume of the box to maintain the target pressure.

Other stuff that’s used:
- Extended Hamiltonian (relating kinetic and potential energies) with additional pressure-volume related terms
- Nose-Hoover Chain thermostat: employed by the Hamiltonian to regulate and allow for fluctuation of temperatures around the desired temp.