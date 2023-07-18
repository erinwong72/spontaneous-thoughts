# JWST pipeline for cosmic ray rejection
The JWST actually uses infrared detectors (the Near-Infrared Spectrograph or NIRSpec), not [[Charge-Coupled Devices|CCDs]]  and measures the signal through an [[Up-the-ramp readout scheme]] which then gets sent to the ground for processing. 

A jump in the signal intensity (measured by the NIRSpec) occurs because of a cosmic ray hit and is manually adjusted for using the jump function from the [jwst package](https://jwst-pipeline.readthedocs.io/en/stable/jwst/jump/description.html). It basically looks for outliers within each integration. But, the manual part is setting the **rejection threshold** of the "difference ratio" (what normal noise/signal should be), which may vary from exposure to exposure.

[Arguments (for jump function)](https://jwst-pipeline.readthedocs.io/en/stable/jwst/jump/arguments.html)
![[Screenshot 2023-07-18 at 12.41.08 PM.png]]