# Up-the-ramp readout scheme

This scheme reads out the intensities of multiple exposures at a time to allow for differentiation between the astronomical source and background signals/noise.

During the series of exposures, the exposure time for each frame increases (it goes *up the ramp*). This is because the astronomical source's signal is dependent on time (varies) while background noise varies much slower. The final measurement is a combination of all the exposures in the series, which is meant to reduce noise.

The readout scheme's actions can be adjusted by **Readout Pattern** options altering three parameters: 1. Frames/group, 2. Groups/integration, 3. Integrations/exposure.

![[Pasted image 20230718123424.png]]

https://jwst-docs.stsci.edu/understanding-exposure-times#UnderstandingExposureTimes-uptheramp