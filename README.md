# equTracer
<br> it is the image to desmos equation converter.
<br> it version 9 of it
#equTracer.py v9 -- image -> Desmos art (centerline tracing)

What changed vs v6:
  v6 built a THICK mask (median stroke ~7 px, 19.7% of the image) and traced
  the contours of that mask.  Every thick stroke became a closed loop hugging
  the stroke, which then got fitted as a skinny ellipse / parabola -> the fat
  black dashes and blobs.  Blur edge effects also filled the image border,
  and Sobel/Frangi/k-means layers fired on faint shading.

# v9 pipeline:
  1. reflect-pad + non-local-means denoise   (JPEG block noise gone, no border)
  2. single scale-space Canny on luminance    (hysteresis => isolated noise dies)
  3. seal 1 px gaps + skeletonize          -> true 1 px lines
  4. graph trace into OPEN paths, prune spurs, drop short/compact specks
  5. smooth -> cubic-Bezier fit (lines when straight, ellipse for full loops)
  6. expression budget keeps the longest / most important strokes
# How setup
<br>
1. download the notebook/file <br>
2. upload it into Google colab <br>
3. click on runtime and change runtime type to T4 gpu <br>
4. run notebook sequence from start. <br>

# Per requirement for upload image
<br> to get the best output 
1. remove the Background of the image
2. make the image contrast to show clear outlines
3. best work with anime or animated images.

# How to export to desmos
1. it will the the 2 file or more as output
2. open the insan.txt file and copy whole equation is desmos equation
3. wait to load
4. click F12 in desmos go to console if can't find press esc
5. open and paste the insane_apply_styles.js content in console
6. if not supported paste the insane_styles_n.txt files content sequentially in consol

# Examples 
<img width="413" height="370" alt="image" src="https://github.com/user-attachments/assets/c5b50e4b-a448-4e51-abfa-91e5e43329e4" />
<img width="366" height="482" alt="image" src="https://github.com/user-attachments/assets/66b65d08-a9e4-43ef-85c5-3e9797f07c07" />
<img width="344" height="513" alt="image" src="https://github.com/user-attachments/assets/654dc4ea-4bf0-40dc-ae41-fc8b47d32e61" />


