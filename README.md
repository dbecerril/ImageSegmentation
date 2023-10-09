# ImageSegmentation (In progress)

We attempt to impliment various image segmentation techniques to better analyze the morphological features of atomic force microscopy measurments of cells. However, these technique could be used for other microscopy methods such as SNOM, elasticity measurments, etc. In the uitlsRF.py we find an implemantion of  the trainable random forest technique as shown in https://scikit-image.org/docs/stable/auto_examples/segmentation/plot_trainable_segmentation.html .

## Trainable Random Forest
 We begin by taking a given AFM image of a cell. We wish to classify each pixel into either glass, cell body or cell nucleus. While in some images this is clear, in others it is only discernible over a given area of the image. We begin by selecting a given region that is clearly glass, cell body or nueclues and feed it to the classifier as training pixels. In this example the pixels in the blue box are used to train the glass classification, those in the red box the cell body and those in green the cell nucleus

![rf_image1](https://github.com/dbecerril/ImageSegmentation/assets/22774966/59555872-8c88-4df0-8323-a80227937512)
