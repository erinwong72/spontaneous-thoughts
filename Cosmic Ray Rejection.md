# Cosmic Ray Rejection

[[JWST pipeline for cosmic ray rejection]]

## Supervised Computer Vision Approach
[[2207.10411.pdf|Cosmic Ray Rejection with Attention Augmented Deep Learning (paper)]] #silo

**Why are cosmic rays so bad?** 
They are basically charged particles (not actually rays) that, when hitting the detector (like [[Charge-Coupled Devices]]), transfers energy to the valence band like photons would (which are the particles you *want* to detect). This leads to potentially mistaking the CR hits as detected sources (maybe even an exoplanet in this project case).

**What are the possible ways to automate CR detection?**
Try getting *multiple* exposures of the same region of the sky because it's very unlikely that the same pixels will be affected by CR hits every time, so you can just compare between exposures. *But*, sometimes getting multiple is not logistically possible, especially when trying to view moving objects.

Single-exposure imaging CR rejection methods have mainly been through identifying abnormalities about CR hits:
1. Brighter and sharper
2. Not blurred like most sources would be
3. Less symmetrical due to coming from any incidence angle

Before ML, Laplacian edge detection in LACosmic had the best performance, but was hand-tuned. 

Using deep learning techniques (computer vision), **image segmentation** can be done to segment out the CR hits, and other artifacts (ghosts, or reflections/scattering of light).

**What are some problems/limitations with the current deep learning implementations?**
**Class-imbalances** making training the model highly inefficient because so few pixels are actually CR hits (as low as 0.027% ;-;). 

The cascade-style framework of the current models waste resources and parameters extracting similar features over and over again.

**How can [[attention gate|attention gates]] be used to address these problems?**
They can suppress activation functions in useless parts of the image and be automatically learned along with the convolutions when the model is trained.