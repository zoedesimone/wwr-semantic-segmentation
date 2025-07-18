# Window to Wall Ratio (WWR) Detection using SegFormer
Official implementation of our [paper](https://arxiv.org/abs/2406.02706).

# Introduction
Window to Wall Ratios (WWR) are key to assessing the performance of buildings, such as the energy consumption, daylight conditions, and ventilation of buildings. Studies have shown that window area has a large impact on building performance and simulation. However, data to set up these environmental models and simulations is typically not available. Therefore, to set up simulations a standard WWR is typically assumed for all buildings, or, at best, it's applied on a building-by-building basis based on initial knowledge regarding the building type and/or age. This paper presents a methodology to predict WWR of buildings from external street view images using semantic segmentation to detect windows and wall regions from images.

# Run the Model on your own images
Use the following Colab notebook to run WWR calculations on your own images using the trained **Segformer** model: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/134owZy0_UB84IxZ4h0x-0uH940Grp3pU?usp=sharing)

Use the following Colab notebook to run Window segmentation on your own images using the trained **FCN** model: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1PpflhuNrAb0RAnFynYf9FCn2Xz2sJHyT?usp=drive_link)

# Trained Model weights
You can find the **FCN** [trained model weights here](https://drive.google.com/drive/folders/1HTOQCSBQIWkj8qrFVfp5pGC6PiQmJBN7?usp=sharing).

You can find the **Segformer** [trained model weights here](https://drive.google.com/drive/folders/1PqjyLutdoXSaGhUr3kYJDzBu12rurLwh?usp=drive_link)

# Dataset Preparation
To generate the dataset we use a publicly available [Window Detection dataset](https://drive.google.com/drive/folders/1TfeIcQ8KlEvP1-ewGcTaj3SqU_IpoLUv) created using LabelMe, consisting of 2806 facade images.

We create two kinds of image pair datasets for the FCN Architecture and the Segformer architecture. 

Original images are resized and normalized for the FCN architecture.

![Figure1](/fig/Figure1.png)

We obtain SegFormer model labels including exterior windows, by using a pre-trained SegFormer with a ResNet50dilated + PPMdeepsup encoder and decoder architecture to detect the building area in the images, and overlay window masks developed for the FCN architecture(above). We converted the output to greyscale masks encoding a single number per pixel, representing the encoded semantic label in the ADE20K semantic categories.

![Figure2](/fig/Figure2.png)

The dataset can be found [here](https://drive.google.com/drive/folders/1_QZlS601vPEbiGORTF3KWj8qoM1H08vo?usp=drive_link), and the code to prepare the Segformer dataset is provided here:
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Z4tDsHpla0bOaCVhvLfztEBwHJkJDP67?usp=sharing)

# Training
We train two models a Fully Convolutional Network (FCN) and a Segformer model, using the two datasets developed for these tasks outlined above.

![Comparison of FCN and Segformer on window segmentation](/fig/visual_results.png)

## Fully Convolutional Network (FCN)
The code to train the FCN can is provided here: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1sYGX06puHNNSfna9eK0h0nC0geY6C1oZ?ouid=101108956433273489124&usp=drive_link).

## SegFormer
The code to finetune the Segformer model is provided here: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1gRHIN5Rz3uwoi09rlp2AdZosWNNCR7ya?usp=drive_link).

# Citation
```
@misc{desimone2024windowwallratiodetection,
      title={Window to Wall Ratio Detection using SegFormer}, 
      author={Zoe De Simone and Sayandeep Biswas and Oscar Wu},
      year={2024},
      eprint={2406.02706},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2406.02706}, 
}
```
