# Cosmic Ray Rejection

[[2207.10411.pdf|Cosmic Ray Rejection with Attention Augmented Deep Learning (paper)]]

## Introduction
**Why are cosmic rays so bad?** 
They are basically charged particles (not actually rays) that, when hitting the detector (like [[Charge-Coupled Devices]]), transfers energy to the valence band like photons would (which are the particles you *want* to detect). This leads to potentially mistaking the CR hits as detected sources (maybe even an exoplanet in this project case).

**What are the possible ways to automate CR detection?**
Try getting multiple exposures of the same region of the sky because it's very unlikely that the same pixels will be affected by CR hits every time, so you can just compare between exposures. But, sometimes getting multiple is not logistically possible, especially when trying to view moving objects.

