[//]: # (Image References)

[image1]: ./images/skin_disease_classes.png "Skin Disease Classes"
[image2]: ./images/options.png "options"
[image7]: ./images/final_ROC_curves.png "Final ROC curve"
[image8]: ./images/multi-model_multi-crop_stats.png "Multi-model statistics"

# Dermatologist AI

## Table of Contents
1. [Introduction](#introduction)
2. [My own algorithm and the resulting scores](#my-own-algorithm-and-the-resulting-scores)
3. [Multi-model and multi-crop statistics](#multi-model-and-multi-crop-statistics)
4. [Getting Started](#getting-started)


## Introduction

In this project, I have designed an algorithm that can visually diagnose [melanoma](http://www.skincancer.org/skin-cancer-information/melanoma), the deadliest form of skin cancer.  In particular, the algorithm distinguish this malignant skin tumor from two types of benign lesions ([nevi](http://missinglink.ucsf.edu/lm/dermatologyglossary/nevus.html) and [seborrheic keratoses](https://www.aad.org/public/diseases/bumps-and-growths/seborrheic-keratoses)). 

The data and objective are pulled from the [2017 ISIC Challenge on Skin Lesion Analysis Towards Melanoma Detection](https://challenge.kitware.com/#challenge/583f126bcad3a51cc66c8d9a).  As part of the challenge, participants were tasked to design an algorithm to diagnose skin lesion images as one of three different skin diseases (melanoma, nevus, or seborrheic keratosis).  

![Skin Disease Classes][image1]

## My own algorithm and the resulting scores

Open [my Jupyter Notebook dermatologist-ai.ipynb](dermatologist-ai.ipynb) to see how I trained multiple Convolution Neural Network to classify the three skin diseases and reached a __Mean ROC AUC score of 0.944__ (see ROC curves for melanoma and seborrheic keratosis below). It would have been a __TOP 1__ in the challenge (see scores in [Evaluation](https://github.com/udacity/dermatologist-ai/blob/master/README.md#evaluation)). It's very satisfying for what I wanted to achieve, especially since the __winner's score is 0.911__.  😃

![Final ROC curve][image7]

But much more than this score, I learned a lot and sometimes the hard way, and took a lot of fun. 😅  
Particularly, I share how I turned my many mistakes while designing the model into positive learning experiences!

## Multi-model statistics

I also found very interesting to make some statisticts on multi-crop / multi-model scores.
A picture is worth a thousand words! Here's the distributions of ROC AUC with respect to number of models:

![Multi-model and multi-crop statistics][image8]

This is interesting to see that __multi-model gives me ≃3.25% return over investment__... whereas multi-crop "only" gives ≃0.6%.

## Getting Started

Click the link below to open and execute my notebook in Google Colab:  

[<img src="https://colab.research.google.com/assets/colab-badge.svg">](https://colab.research.google.com/github/sebastienlange/dermatologist-ai/blob/master/dermatologist_ai.ipynb)
  
Ensure GPU is enabled: Edit > Notebook settings or Runtime>Change runtime type and select GPU as Hardware accelerator

In the Notebook's Getting Started, change settings according to your needs:  
![options][image2]

Then press Ctrl+F9 to Execute all cells in the notebook

Be patient, it takes +/-3\* minutes (if download_images=False) or +/- 12 minutes (if download_images=True) to execute all the notebook cells including : 
- 5' to download and 3' to extract default images
- 1' to download and extract additional images
- 1' to download results for all pretrained models
- 1' to build the best team
- 1' to execute all other cells around (1')  
_* timing is of course approximate, and estimated on NVIDIA Tesla T4 GPUs, which is faster than the older NVIDIA Tesla K80 GPU my models were trained on_

Optionally add +/- 16 minutes if you want to skip loading results and force testing, as the very first time it requires to resize all images. And 1 more minute to test DenseNet, and up to 4 minutes for NasNetALarge...

Optionally Add many hours if you want to train your own model... 😊  
Note that my models were trained with NVIDIA Tesla K80 GPU.

If you want to know more details about the challenge itself, or create your own project from scratch, read the [original README.md](https://github.com/udacity/dermatologist-ai/blob/master/README.md).
