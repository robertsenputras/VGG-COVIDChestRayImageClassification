# VGG-COVIDChestRayImageClassification
This repo comes from a final project of Fundamental of Control and Intelligence System at Institut Teknologi Bandung
by: Robertsen Putra Sugianto

## Background

COVID-19 is a pandemic with a very fast spreading time and symptoms common with other coronavirus diseases. The key to this pandemic is early and accurate detection so that its spread can be suppressed. One method detection of COVID-19 besides PCR and rapid test is the detection of COVID-19 in the image CXR.

## Problem:

- The existence of false negative detection by PCR at the beginning of infection CXR (Chest X-ray) images can be complementary to the initial PCR results so as to reduce false negatives as much as possible.
- The PCR process is more accurate, but takes a long time and not many labs in Indonesia are capable. Radiology images tend to be fast and can be done anywhere.

## Why should use X-Ray
COVID-19 is a viral infection that can experienced by anyone. X-rays has the advantage of being cheap and price fast; therefore, X-rays are easier accessed by health care providers who work in a small area and / or isolated. This model is a prototype system and not for medical use and cannot be used for diagnosis yet.

## Dataset
The number of datasets used in this task is as many as 266 pieces of CXR images, with information:
- 160 thorax data for COVID-19 patients
- 106 normal thorax data

<p align="center">
<img src="https://github.com/robertsenputras/VGG-COVIDChestRayImageClassification/blob/main/fig/dataset-biasa.png"  width="700" height="400">
</p>
<p>
  <em>Normal x-ray images<em>
</p>
<p align="center">
<img src="https://github.com/robertsenputras/VGG-COVIDChestRayImageClassification/blob/main/fig/dataset-covid.png"  width="700" height="400">
</p>
<p>
  <em>Covid x-ray images<em>
</p>
    

## Description of the training method
Deep Learning method is used to do classification of Pneumonia (Covid-19) on radiological images by looking for signs of appearance infiltrates / opacities / consolidation.

### Architecture
Transfer learning method is used using the pretrained model VGG16 have been trained using the Imagenet dataset. VGG-16 is a CNN architecture, used for feature extraction in the image. Pretrained VGG-16 as the base model, then add a new model(trainable) on the final layer of VGG-16.

<p align="center">
<img src="https://github.com/robertsenputras/VGG-COVIDChestRayImageClassification/blob/main/fig/vgg.png"  width="700" height="300">
</p>

**The covid19 Plot Model used in this project. There is a change in the number of neurons in the dense_8 layer from 64 to 128**

## Training and Hyperparameter tuning

By using this dataset, **training accuracy** is obtained around **90%**. Sklearn library with *GridSearch* class is used to sweep some of the optimum values of hyperparameters. This sweeping starts with **coarse tuning and fine tuning**. The following results were obtained:

## Result
- Learning Rate (LR) = 0.008
- Batch Size (BS) = 7
- Epoch = 12
- Optimizer = Adam

Grid Search supports the K-fold cross validation feature which is used to prevent overfitting. Adam optimizer is used because it includes RMSprop and Adagrad as well.

## Evaluation
Accuracy = 0.9815
Precision = TP / (TP + FP) = 0.97
Sensitivity = TP / (TP + FN) = 1,000
Specificity = TN / (TN + FP) = 0.9545
