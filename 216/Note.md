# COMPSCI 216
## 1/11
What is conputer vision? \
The study of extracting information from visual data \
**radiance**
Light going out (watt per united direction per unit surface area) \
**irradiance**
Light coming in watt per unit surface area 

## 1/23 
**human shape perception**
Psychophysics: studying of how people proceed things. \
diffuze surface, an eye is looking from above and a light shines on it. \
can integrate the normal estimates from peoeple (not all people see the same shape in regions). \ 
bas-relief ambiguity \
What is the space of images of an object under all illuminations? \
Fix all camera fix the objection, change illumination \
at least 3 illuminations to produce a image cone \
What is consistent across illuminations? \
Cracksm crevicesm high contrast edges. \

## might be on exam
**Why is recognition difficult (in computer vision)?** \
No "off the shelf" function for every object \
Variation in appearence: lighting, pose, viewpoint(3D) \
pose: articulation deformation \
Same thing looks different & different things look the same 

**Why is it difficult to learn a function to recognize images of things** \
**Why is it difficult to learn from pixels?** \
very high dimensional:
- everything is equally far away in pixel space
- never have enough densely cover the range of things
- pixels change fast relative to perception, so our object has high curveture 
- pixels are dumb 

**Why does recognition ever work?** \
There exist features that are better than raw pixels
- more robust (lower curvature)
- still discrimitive
  - e.g. edges, corners, gradient orientation, histogram of gradient
- deep learning works
  - 2012 alex net: fast compute, big network, image net challenge dataset(large labeled dataset), 
  - convolution nets + ReLu
  - generalized to other problem (fine tuning)

**Image classification, object detection, human pose, segmentation** \
is there a dog in the image? \
put a box + score around dog in the image \
we do:
- take input and consider possible boxes for the target predict Y/N for each.
- simplify output e.g. non-max suppression find the best output(find the box that has the best score)
- single shot detector(SSD) simplifies the space by classifying a large box and regressing the object location

## Evaluate detection
non-max suppression, sort score for a class over all boxes. \
if intersection over union of my output and anything higher than me > threshold -> suppress. \
2 boxes, if one on top of another, threshold = 1 \
2 boxes, if disjoint, threshold = 0 \

## Discriminately trained part model for detection
structure prediction, latent variable model \
wF(x, y) x is input image y output, pos, binary label. \
Latent variable model wF(x,L)

more powerful deep learning gets us away from imposing structure in parts/poses/features \
- Training network can be hard/expensive
- still have some hand designed structure
- 