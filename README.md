# ImageSegmentation (In progress)

We attempt to impliment various image segmentation techniques to better analyze the morphological features of atomic force microscopy measurments of cells. However, these technique could be used for other microscopy methods such as SNOM, elasticity measurments, etc. In the "RandomForest" notebook we find an implemantion of  the trainable random forest technique as shown in https://scikit-image.org/docs/stable/auto_examples/segmentation/plot_trainable_segmentation.html .

## Trainable Random Forest
 We begin by taking a given AFM image of a cell. We wish to classify each pixel into either glass, cell body or cell nucleus. While in some images this is clear, in others it is only discernible over a given area of the image. 

![rf_image1](https://github.com/dbecerril/ImageSegmentation/assets/22774966/59555872-8c88-4df0-8323-a80227937512)

We begin by selecting a given region that is clearly glass, cell body or nueclues and feed it to the classifier as training pixels. In this example the pixels in the blue box are used to train the glass classification, those in the red box the cell body and those in green the cell nucleus. We then run the image through a series of filter and classify each pixel based on those filter. 

![rf_image2](https://github.com/dbecerril/ImageSegmentation/assets/22774966/728473be-c1f8-4827-991c-4c119d5dbc48)

The above image shows the classificacion based on the  training pixels of image 1. A further post processing is still needed to "close" the holes in each section and separate overlapping cells.

## Hessian with Chan-Vese method
When analysing different types of cell lines, differentiating Cell body and cell nucleus based soley on morphological features can become challenging. This can introduce error due to the subjectivity of the cell body segmentation. To overcome this we try a cell segmentation based ont the following method. 
1.- Preprocessing: reducing artefact introduced by the AFM microsocpe.
2- Identificaction of the cell within the image 
3.- Calculation of Hessian eigenvalues for each pixel in image and definition of "seed mask" using the Hessian Method.
4.- Growing of mask using the Van- Chese method as shown in Chan and Vese "Active contours without edges" 10.1109/83.902291. 

We consider an example of an U2 osteosarcoma cell line.
