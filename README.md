# Window to Wall Ratio (WWR) Detection using SegFormer
Official implementation of our paper.

# Introduction
Window to Wall Ratios (WWR) are key to assessing the performance of buildings, such as the energy consumption, daylight conditions, and ventilation of buildings. Studies have shown that window area has a large impact on building performance and simulation. However, data to set up these environmental models and simulations is typically not available. Therefore, to set up simulations a standard WWR is typically assumed for all buildings, or, at best, it's applied on a building-by-building basis based on initial knowledge regarding the building type and/or age. This paper presents a methodology to predict WWR of buildings from external street view images using semantic segmentation to detect windows and wall regions from images.

# Dataset Preparation

To generate the dataset we use a publicly available [Window Detection dataset](https://drive.google.com/drive/folders/1TfeIcQ8KlEvP1-ewGcTaj3SqU_IpoLUv) created using LabelMe, consisting of 2806 facade images.

We create two kinds of image pair datasets for the FCN Architecture and the Segformer architecture. 

Original images are resize and normalized for the FCN architecture.
![Figure1](/fig/Figure1.png)

We obtain SegFormer model labels including exterior windows, by using a pre-trained
SegFormer with a ResNet50dilated + PPMdeepsup encoder and decoder architecture to detect the building area in the images, and overlay window masks developed for the FCN architecture(above). We converted the output to greyscale masks encod-
ing a single number per pixel, representing the encoded semantic label in the ADE20K semantic categories.
![Figure2](/fig/Figure2.png)

The dataset can be found here, and the code to prepare the Segformer dataset can be found here.

# Training

# Examples

