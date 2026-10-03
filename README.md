# epuTracer
<br> it is the image to desmos equation converter.
<br> it version 7 of it
#equTracer.py v7 -- image -> Desmos art (centerline tracing)

What changed vs v6:
  v6 built a THICK mask (median stroke ~7 px, 19.7% of the image) and traced
  the contours of that mask.  Every thick stroke became a closed loop hugging
  the stroke, which then got fitted as a skinny ellipse / parabola -> the fat
  black dashes and blobs.  Blur edge effects also filled the image border,
  and Sobel/Frangi/k-means layers fired on faint shading.

# v7 pipeline:
  1. reflect-pad + non-local-means denoise   (JPEG block noise gone, no border)
  2. single scale-space Canny on luminance    (hysteresis => isolated noise dies)
  3. seal 1 px gaps + skeletonize          -> true 1 px lines
  4. graph trace into OPEN paths, prune spurs, drop short/compact specks
  5. smooth -> cubic-Bezier fit (lines when straight, ellipse for full loops)
  6. expression budget keeps the longest / most important strokes

# Per requirement for upload image
<br> to get the best output 
1. remove the Background of the image
2. make the image contrast to show clear outlines
3. best work with anime or animated images
