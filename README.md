# Edge Enhanced GAN For Remote Sensing Image Superresolution (EEGAN)

This is an implementation of the SRGAN model proposed in the paper
([Edge Enhanced GAN For Remote Sensing Image Superresolution](https://ieeexplore.ieee.org/document/8677274))
with TensorFlow.

# Requirements

- Python 3
- TensorFlow 1.1(GPU)
- OpenCV
- tqdm 

# Usage

## I. Pretrain the VGG-19 model

Download the ImageNet dataset and preprocess them with:

```
$ cd vgg19/imagenet
$ python get_urls.py
$ python create_db.py
$ python download_images.py
$ python preprocess.py
```

Train with VGG-19:

```
$ cd vgg19
$ python train.py
```

Or you can download the pretrained vgg19 model file from 
([Google Drive](https://drive.google.com/open?id=0B-s6ok7B0V9vcXNfSzdjZ0lCc0k) and [Baidu](https://pan.baidu.com/s/1ToKro4y-lRBQuauDuc2zhQ), password:hooj)


## II. Train the EEGAN model

Train with EEGAN:

Download the satellite image from [Kaggle Open Source dataset](https://www.kaggle.com/c/draper-satellite-image-chronology/data) and preprocess them to obetain the training samples with 

```
$ cd src/lfw
$ python preprocess.py
```

Then train the model EEGAN with:
```
$ cd src
$ python train.py
```

The evaluation results will be stored in "src/result".

Test with EEGAN:

The pretrained weight can be downloaded from [weight file](https://drive.google.com/file/d/1HeQBXE67urcKOJv0GfmJBsA0zZznAAwn/view?usp=sharing).

Put the test images into "src/test/test30" or your own folder, then
```
$ cd src/test
$ python test.py
```

The tes results will be stored in "src/test/result30".


# Results

## Kaggle


# Loss function

## Adversarial loss 

This implementation adopts the least squares loss function instead 
of the sigmoid cross entropy loss function for the discriminator.
See the details: [Least Squares Generative Adversarial Networks](
https://arxiv.org/abs/1611.04076)

## Content loss

The paper says VGG54 is the perceptually most convincing results.
But this implemetation uses all the feature maps generated by every layer
(i.e. phi12, phi22, phi34, phi44, phi54) within the VGG19 network.


## Consistency loss


## If you find our work useful in your research or publications, please consider citing:
```
@ARTICLE{8677274,
  author={K. {Jiang} and Z. {Wang} and P. {Yi} and G. {Wang} and T. {Lu} and J. {Jiang}},
  journal={IEEE Transactions on Geoscience and Remote Sensing}, 
  title={Edge-Enhanced GAN for Remote Sensing Image Superresolution}, 
  year={2019},
  volume={57},
  number={8},
  pages={5799-5812},
  doi={10.1109/TGRS.2019.2902431}}
```
