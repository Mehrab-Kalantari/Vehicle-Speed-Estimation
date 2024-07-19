# Vehicle Speed Estimation from Video 

[Related article on medium](https://medium.com/@selfouly/vehicle-speed-estimation-from-video-using-deep-learning-18b41babda4c)

[Dataset on github](https://github.com/commaai/speedchallenge)



This task contains two main steps
1. Loading the video and converting it to its consecutive frames and then calculating displacements using optical flow pre-trained models
2. Creating a CNN to predict speed from displacements
---

## First Step) Optical Flow Estimation
Here we firstly load the video and convert it to its frames and save them.
This process is done for both train and test separately.

There are 20400 frames for train and 10798 frames for test.

**Frame sample**
* ![frame](samples/frame%20sample.png)


Now that frames are ready, it is time to estimate flow using optical flow estimation models.

The approach we have chosen is **RAFT: Recurrent All-Pairs Field Transforms for Optical Flow**.

There are two reasons that have led to this choice:
1. RAFT was trained on KITTI dataset which includes scenes captured from a car driving through urban environments, making it suitable for our task.
2. It is robust to noise and brightness change which was mentioned before.



[Paper link here](https://arxiv.org/pdf/2003.12039)



[Official github implementation](https://github.com/princeton-vl/RAFT?tab=readme-ov-file)

**Displacements sample**
* ![dis](samples/flow%20sample.png)

## Flow Preprocessing
Before creating the model, due to the huge load of data we need to preprocess it and save images as **.npy** file.
Every image has been resized and normalized.

---
## Second Step) Speed Estimation with CNNs

Here we load the dataset and try some famous pre-trained models such as:
* ResNet18
* EfficientNet


