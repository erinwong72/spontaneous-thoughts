# MinHash fingerprint

A way to estimate **Jaccard similarity** without having to use many computational resources comparing every element in the set to each other.

1. Slides a “shingle” or window spanning several characters or object, over the entire set, for both
2. Apply a function (a “hash”) to all shingles
3. Take minimum (or multiple)
4. Repeat if you use more than one hash (can also just use one and take n lowest values)
5. MinHash = overlapping values/n