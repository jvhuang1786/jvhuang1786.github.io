---
layout: archive
permalink: /GANS/
title: "MHXX and Anime GANS"
author_profile: true
header:
  image: "/mhxximg/title1.png"
---

# Generative Adversarial Networks Improving the creation Pipeline

  * Concept design can take time. The goal of this project is to see if we can
  make the creative process more efficient.  

<img src="{{ site.url }}{{ site.baseurl }}/mhxximg/gan.png" alt="GAN, capcom, mhxx" width="800" height="800">


## Compute Requirements

  * GPU Nvidia Requirements
    - Nvidia GPU 11 gb and above
    - tensorflow-gpu 1.1.5
    - cuda 10.0
    - cuDNN 7.5
    - tensorRT 5.6.5


## Data Augmentation

  * Libraries
      - numpy
      - os
      - cv2
      - glob
      - pandas
      - PIL
      - scipy
      - imageio
      - keras
      - augmentor
      - fastai

  * Anime faces and MHXX armor images were collected.

     * The anime face data set was collected on kaggle and had 85000 images
     * MHXX was collected from a fan website and had 1083 images

  * To increase the size of the MHXX armor data set we had to do the following

      1. Split the double images and put back the single images
      2. Get rid of only top half images
      3. Mirrored the Images
      4. Did random sampling of brightness and dimness of 0.7 to 1.2
      5. The data increased to 19437 and then used photoshop to inrease resolution
      6. Used augmentor to turn them to 512 x 512 dimensions
      7. Use fastai to check if it can pass through Nvidia's dataset_tool.py
      8. Changed to tfrecords.     

<img src="{{ site.url }}{{ site.baseurl }}/mhxximg/augment.png" alt="GAN, capcom, mhxx" width="800" height="800">

## Feature Map Exploration

  * Libraries
      - keras.applications.vgg16
      - keras.preprocessing.image
      - matplotlib
      - numpy

  * We used a model in keras vgg16 which is a convolutional neural network.  

  * Wanted to see the activation map of one of our images.

  * Further from input the less detail

  <img src="{{ site.url }}{{ site.baseurl }}/mhxximg/featuremap.png" alt="GAN, capcom, mhxx" width="800" height="800">


## Deep Convolutional Generative Adversarial Networks

  * Libraries
      - numpy
      - os
      - glob
      - imageio
      - time
      - PIL
      - keras
      - matplotlib


<img src="{{ site.url }}{{ site.baseurl }}/mhxximg/dcgan.png" alt="GAN, capcom, mhxx" width="800" height="800">

  * DCGAN was a quick way to visualize our image datasets.

  * Uses convolutional layers.  Conv2DTanspose for Generator, Conv2D for Discriminator

  * Used original learning rate from paper.

  * Ran it for 2000 steps

  <img src="{{ site.url }}{{ site.baseurl }}/mhxximg/armor2000.png" alt="GAN, capcom, mhxx" width="800" height="800">

  <img src="{{ site.url }}{{ site.baseurl }}/mhxximg/face2000.png" alt="GAN, capcom, mhxx" width="800" height="800">

* 20000 Training Steps

<img src="{{ site.url }}{{ site.baseurl }}/mhxximg/mhxx.gif" alt="GAN, capcom, mhxx" width="800" height="800">

* Generator Loss, Discriminator Fake Loss, Discriminator Real Loss

<img src="{{ site.url }}{{ site.baseurl }}/mhxximg/dcgann_loss.gif" alt="GAN, capcom, mhxx" width="800" height="800">


# Frechet Inception Distance

  * Libraries
      - numpy
      - scipy
      - keras
      - skimage.transform
      - imblearn

  * Looks at the normal distribution of real images vs fake images.  The lower number the better.


## Style GAN

  * Libraries
    - numpy
    - tensorflow
    - dnnlib
    - config
    - train
    - training
    - copy
    - metrics

<img src="{{ site.url }}{{ site.baseurl }}/mhxximg/sgan.png" alt="GAN, capcom, mhxx" width="800" height="800">

* First trained the anime face model using the preset hyperparameters.

<img src="{{ site.url }}{{ site.baseurl }}/mhxximg/animeface.gif" alt="GAN, capcom, mhxx" width="800" height="800">

* Stopped at 7 days of training.

<img src="{{ site.url }}{{ site.baseurl }}/mhxximg/fakes007440.png" alt="GAN, capcom, mhxx" width="800" height="800">

* Tried to train from scratch to see if I could get similar results with the armor images

* Mode collapse from mainly b/c too small of a dataset

<img src="{{ site.url }}{{ site.baseurl }}/mhxximg/fakes007140.png" alt="GAN, capcom, mhxx" width="800" height="800">

* Used Transfer Learning with pickled model with anime faces

* Halved learning rate and decreased mini batch repeat to 1

<img src="{{ site.url }}{{ site.baseurl }}/mhxximg/fakes007680.png" alt="GAN, capcom, mhxx" width="800" height="800">

* End Result using interpolation

<img src="{{ site.url }}{{ site.baseurl }}/mhxximg/armor_morph.gif" alt="GAN, capcom, mhxx" width="800" height="800">


## Image Generator and MP4 creation

  * Libraries
    - glob
    - numpy
    - moviepy
    - os
    - PIL
    - dnnlib
    - pickle

<img src="{{ site.url }}{{ site.baseurl }}/mhxximg/vidstich.png" alt="GAN, capcom, mhxx" width="800" height="800">


  * Full write up, blog post and github link can be found below.


  [MHXX GAN Blog post](https://jvhuang1786.github.io/MHXXGAN/)


  [MHXX GAN Write Up](https://docs.google.com/document/d/1pgZfQyXih_lmArl-OqA81ylXD48rHplDr4idt_k2seQ/edit)


  [MHXX GAN Github](https://github.com/jvhuang1786/mhxxCapStone)
