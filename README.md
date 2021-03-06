# Introduction

In this project, I implemented an action recognition system which can recognize 5 types of human action: kick, punch, stand, wave, squat.

# Installation

check the: settings/library.txt: [here](https://github.com/TheK2NumberOne/action-recognition-project/blob/master/action-recognition-using-pose%20estimation-2D/setting/library.txt)

# Run real-time action recognition

> python3 src/run_detector.py --images_source webcam

# Implementation

Have 5 types of action: kick, punch, stand, wave, squat. The length of each video about 2 minutes and each video only contains one type of action with a frame size of 640x480, and then saved to images.

# Get skeleton from image

I used OpenPose to detect the human pose in each training images.

The output skeleton format of OpenPose can be found at [OpenPose Demo - Output](https://github.com/CMU-Perceptual-Computing-Lab/openpose/blob/master/doc/output.md).

The generated training data files are located in data folder:

+ [skeleton_raw.csv](https://github.com/TheK2NumberOne/action-recognition-project/blob/master/action-recognition-using-pose%20estimation-2D/data/skeleton_raw.csv): original data

+ [skeleton_filtered.csv](https://github.com/TheK2NumberOne/action-recognition-project/blob/master/action-recognition-using-pose%20estimation-2D/data/skeleton_filtered.csv): filtered data where incomplete poses are eliminated

# Data processing

1. Remove all joints on head: because all joint positions on head are not required for action recognition task.

2. Normalization: all joint positions are converted to the x-y coordinates relative to the skeleton bounding box.

# Deep learning model

I built a neural network by using Keras. the model consists of three hidden layers and a softmax output layer to conduct a 5-class classification.

The model implemented in [action_training.ipynb](https://github.com/TheK2NumberOne/action-recognition-project/blob/master/action-recognition-using-pose%20estimation-2D/src/Training_action.ipynb).

The generated model is saved in [model](https://github.com/TheK2NumberOne/action-recognition-project/tree/master/action-recognition-using-pose%20estimation-2D/model) folder.

You can replace Fully connected neural network with a LSTM network for higher performance.

# Acknowledgement

   [tf-pose-estimation](https://github.com/ildoonet/tf-pose-estimation)
    
   [Human Pose Estimation Benchmarking and Action Recognition](https://github.com/ChengeYang/Human-Pose-Estimation-Benchmarking-and-Action-Recognition)
