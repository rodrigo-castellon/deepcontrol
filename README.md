# DeepControl

## [LINK TO PUBLIC DATASET](https://drive.google.com/drive/folders/1SjSheeJO09zaGBIkAiLw6ToQiecFdm4i?usp=sharing)

Here's the link to the dataset mentioned in the paper.

### Abstract

Historically, businesses and governments have hesitated to digitize their legacy systems and infrastructure (power plants, data centers, etc.) because of the enormous costs associated with this transition, including the overhaul of rigorously tested mechanical equipment and systems that have been operating reliably for decades. The digitization of infrastructure presents clear benefits over the rigid but stable operation of legacy systems, including the ability to remotely control and oversee operation, implement predictive machine learning algorithms to anticipate component breakdown, and optimize mechanical processes. This research presents an alternative, scalable, and adaptable deep learning control system that uses a webcam feed to operate a control task on a “legacy” computer. To achieve this, the system uses supervised learning/behavioral cloning to train an 8-layer convolutional neural network (CNN) on expert human gameplaying data of the control task (a driving simulator). This CNN serves as the intelligence for the system. Furthermore, a microcontroller interface was developed to allow the system to carry out its predicted actions in-game; the interface connected the CNN to the “legacy” computer, allowing the CNN to control the game. When trained and tested on a task of completing an oval road course, the CNN manages to achieve near human performance in lap time, average speed, and top speed. In the future, an end-to-end control system similar to ours that  exploits CNNs’ ability to map noisy optical input to appropriate actions could bridge the gap between legacy systems and the digital world.


## Brief Overview

A project to create a deep learning control system that learns by an air-gapped optical input stream rather than raw pixels. Applications include all sorts of infrastructure with legacy hardware (flood control, manufacturing plants, power plants).

Specifically, below is the configuration.

![configuration](http://imgur.com/gmTRUSn.jpg)

## Policy Network Procedure
### *Collection*
#### 1. Run `policy_collect.py` to collect data.
This will store corresponding image frames and keypresses at every timestep into .h5 files in a "dataset" folder. It will store it in batches of 500 frames as one .h5 file, and to toggle data collection press the spacebar.

#### 2. `Run deleteblankframes.py`
Since the policy_collect.py script produces extraneous blank frames, run `deleteblankframes.py` to delete them to prepare for policy network training.

#### 3. Adjust and Drag to /dataset/ folder
Drag collected data in the `/sim-datasets/datasetname/fixed/fixed/` to `/dataset/`, renaming it with `dataset_rename.py` if needed.


### *Training*
Run `policy_train.py` to train on data collected in `/dataset/`. 

### *Real-time evaluation*
Run `policy_run.py` to run on the trained neural network and control the simulator in real-time.

## Some Figures/Results

![accuracy](https://github.com/mpcrlab/DeepControl/raw/master/plots/12-1training_accuracy.png)

![loss](https://github.com/mpcrlab/DeepControl/raw/master/plots/12-1training_loss.png)

![screenshot1](https://github.com/mpcrlab/DeepControl/raw/master/opticalscreenshot.png)
