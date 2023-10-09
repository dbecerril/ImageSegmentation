# ImageSegmentation (In progress)

We attempt to impliment various image segmentation techniques to better analyze the morphological features of atomic force microscopy measurments of cells. However, these technique could be used for other microscopy methods such as SNOM, elasticity measurments, etc. In the "RandomForest" notebook we find an implemantion of  the trainable random forest technique as shown in https://scikit-image.org/docs/stable/auto_examples/segmentation/plot_trainable_segmentation.html .

## Trainable Random Forest
 We begin by taking a given AFM image of a cell. We wish to classify each pixel into either glass, cell body or cell nucleus. While in some images this is clear, in others it is only discernible over a given area of the image. 

![rf_image1](https://github.com/dbecerril/ImageSegmentation/assets/22774966/59555872-8c88-4df0-8323-a80227937512)

We begin by selecting a given region that is clearly glass, cell body or nueclues and feed it to the classifier as training pixels. In this example the pixels in the blue box are used to train the glass classification, those in the red box the cell body and those in green the cell nucleus. We then run the image through a series of filter and classify each pixel based on those filter. 

![rf_image2](https://github.com/dbecerril/ImageSegmentation/assets/22774966/728473be-c1f8-4827-991c-4c119d5dbc48)

The above image shows the classificacion based on the  training pixels of image 1. A further post processing is still needed to "close" the holes in each section and separate overlapping cells.

## Hessian with Chan-Vese method
When analysing different types of cell lines, differentiating Cell body and cell nucleus based soley on morphological features can become challenging. This can introduce error due to the subjectivity of the cell body segmentation. To overcome this we try a cell segmentation based ont the following method which is found in the "segmentation_v0.ipynb" notebook. The method consists of: 

1.- Preprocessing: reducing artefact introduced by the AFM microsocpe.

2- Image size redution, gaussian blurring and calculation of hessian for each pixel in image

3.- Calculation of Hessian eigenvalues for each pixel in image and definition of "seed mask" using the Hessian Method.

4.- Growing of mask using the Van- Chese method as shown in Chan and Vese "Active contours without edges" 10.1109/83.902291. 



We consider an example of an U2 osteosarcoma cell line. The first image shows a preprocessed image taken from the AFM microscope in which a cell has been centered and afm artefacts have been removed.

![van_chese_1](https://github.com/dbecerril/ImageSegmentation/assets/22774966/7d54d2c8-c348-4b05-a2ff-3326161733a3)

We then carry out steps (2) and (3)

![van_chese_2](https://github.com/dbecerril/ImageSegmentation/assets/22774966/2becc394-e875-48e7-bc03-1f810198ef6b)

Growing the seed mask we obtain a segmentation of the nucleus based soley on the cell morphology

![van chese 3](https://github.com/dbecerril/ImageSegmentation/assets/22774966/4a9b2c28-4a04-4dc8-905f-114e1ff13c32)

Further methods are being tested to improve the segmentation and also carry out a segmentation of cell body.

# Acknowledgment
D. Becerril acknowledges financial support from the Mexico City Ministry of Education, Science, Technology and Innovation (2023).



