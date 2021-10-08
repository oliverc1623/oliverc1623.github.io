# CS152 Project Outline

## Name:

Crossing the Reality Gap

## Group Members:

- Tony Revilla
- Max Rose
- Oliver Chang

## Outline:

Neural networks are becoming an increasingly useful tool in autonomous navigation, but it is expensive so we turn to simulations. 

Over the summer, the ARCS lab surveyed multiple CNN architectures in the Raycasting simulation. Next, we seek to implement a more robust model in an Unreal simulation. 

The Raycasting simulation is computationally cheap to run, but sacrifices high definition detail. Hence, we will continue the same data collection methods in Raycasting, but apply them to Unreal.

Given we’ll be working with two environments, it is imperative that we synchronize our data collection methods, CNN implementation, and data analysis. 

Ideally, a model trained in the unreal engine should be able to traverse the Raycasting simulation and real-life autonomously. 

## Ethics:

Since we are working with autonomous robots, we seek to create a product that will never inflict harm on other humans. More specifically, this technology should not be used as weapons of war in destructive ways.

# Literature Review

## [**Driving Policy Transfer via Modularity and Abstraction**](https://arxiv.org/pdf/1804.09364.pdf)

This paper aims to bridge the reality gap through modularity and abstraction. Paper used CARLA, which is an open-source urban driving simulator. The paper implemented an encoder-decoder CNN with a perception system. This perception system takes in images from a camera but segments the image into "road" and "non-road" components.

## [**Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks**](https://openaccess.thecvf.com/content_ICCV_2017/papers/Zhu_Unpaired_Image-To-Image_Translation_ICCV_2017_paper.pdf)

Unpaid image-to-image translation converts an image from one representation to another. This paper implemented this technique with a cycle generative adversarial network. This network includes a loss function that uses cycle consistency loss. The researchers found positive results when translating colors and texture. However, they note that geometric changes found little success.

## [**UnrealCV: Connecting Computer Vision to Unreal Engine**](https://link.springer.com/content/pdf/10.1007/978-3-319-49409-8_75.pdf)

Computer graphics can construct virtual worlds that allow different agents to simulate interactions in different environments. This group uses Unreal Engine 4 to construct a tool, UnrealCV, that allows researchers to construct virtual worlds and connect a neural network to an agent in a world, allowing the network to train from the simulated data and direct the agent.

## [**RoboTHOR: An Open Simulation-to-Real Embodied AI Platform**](https://arxiv.org/abs/2004.06799)

This paper introduces RoboTHOR, a platform that helps develop and train agents on various AI navigation tasks in simulated environments and enables testing in both the simulation and the real world. The paper discusses the many challenges associated with the nature of transferring learning between real and simulated worlds. As a platform, RoboTHOR aims to overcome these many challenges by providing an accessible and replicable system that focuses on the learning between simulated spaces and its corresponding physical environment. Initial experimentation has shown that there still is a large gap to overcome, but they hope RoboTHOR will narrow the gap as it’s continually used and updated.

# Update One

## Name and link of the software we will use

- [UnrealEngine](https://www.unrealengine.com/en-US/)
- Plugins include [UnrealCV](https://unrealcv.org/)
- [Raycasting Simulator](https://github.com/anthonyjclark/raycasting-simulation)
- [Python](https://www.python.org/)
- [FastAI](https://www.fast.ai/) & [PyTorch](https://pytorch.org/)

## Name and link to dataset

- Set of images collected with the wandering automator inside of the UnrealEngine. We will create this by using the Raycasting automator tailored to UnrealEngine. The dataset size will start with 10,000. This will serve as a proxy. If things go well, we’ll increase our dataset to 100,000. 
- We can use the dataset from the Raycasting simulation project over the summer for consistency

## Overview of the following

### Type of Neural Network

We will use a convolutional neural network for the naive maze navigation. We’ll use the XResNeXt18, XResNeXt50, and AlexNet architectures since they performed the best in the Raycasting simulation. Additionally, we'll use a Generative adversarial network for raycasting to Unreal image-to-image translation. 

### Shape and size of inputs
Images will be 224x224 and they are RGB pngs they are three-channel images 

### Shape and type of outputs
The neural network will have two types of outputs. One is an integer indicating left, right, and straight. This will tell us which direction to turn in. This is a classification output.
The second output is a continuous value, which tells us which angle to turn at. This is a regression output.