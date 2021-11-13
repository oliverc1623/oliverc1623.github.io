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

# Introduction

With improving technology, graphics processing units (GPUs) are utilized more in computer graphics. One field that has reaped the benefits of GPU improvement is simulations. Physics simulations that required data parallelism and intensive computation are now more accessible than ever. One application of simulation is in autonomous navigation. The high cost of building and maintaining a robot that can autonomously traverse terrain makes it challenging to implement computational intelligence. One way to test artificial intelligence in robots is through simulations. We are interested in examining neural network performance across different simulations and real life. In particular, we are looking to see how an agent can traverse a maze using a neural network (NN). We want to observe a robot learn to navigate a terrain, identifying a path to reach a goal. 

NNs are useful in that we can feed in images to a model and have it return a direction for which a robot can interpret and move accordingly. For this cross-simulation experiment, we have selected a handful of architectures that were trained in a Raycast simulation. We believe they will cross the reality gap best in the Unreal simulation. Such architectures include ResNet, AlexNet, and an original architecture that takes an image and concatenates the previous command string. The Unreal simulation serves as a proxy for how well the models might perform in real life. We first demonstrate raycasting model performance in the Unreal simulation. After, we train models in the unreal simulation and observe their performance in the raycasting simulation. Finally, we apply a Cycle-GAN translation to generate a synthetic dataset that merges two simulations. 

# Related Works

Neural Networks have been shown to be effective at navigating agents in different environments. However, successful training of the model often requires large quantities of training data, and in many scenarios gathering this data with real world testing may be difficult. Therefore, many researchers have attempted to create synthetic data of their specific environment in order to train more complicated models. This has shown to be an effective training method in many cases.

Weichao [Qiu](https://link.springer.com/content/pdf/10.1007/978-3-319-49409-8_75.pdf) and Alan Yuille created UnrealCV, a tool built on Unreal Engine 4 that allows researchers to build a virtual world, and then extract the information collected by an agent in that world to be used in a neural network. This model can then be used to send information back to the agent to perform tasks in the virtual world.

Chang et al. built a simulation to collect data to train many models to evaluate their resulting behaviors. The data was collected from the simulation, and different data collection techniques were studied to determine the most effective strategy. It was found that the models performed well in the given simulation, they fail when the simulation environment is altered in various small ways.

[Deitke et al.](https://openaccess.thecvf.com/content_CVPR_2020/html/Deitke_RoboTHOR_An_Open_Simulation-to-Real_Embodied_AI_Platform_CVPR_2020_paper.html) introduces RoboTHOR, a platform that helps develop and train agents on various AI navigation tasks in simulated environments and enables testing in both the simulation and the real world. The paper discusses the many challenges associated with the nature of transferring learning between real and simulated worlds. For this project, we seek to tackle this challenge demonstrated in the paper. Specifically, we turn to UnrealEngine to provide a high quality simulation environment to ease the transitions. We are interested in seeing if the lighting and higher quality graphics from the game can help the neural network travel through the maze in real-life in similar settings. 

# Project Milestone 6: Update 2

- What have you completed or tried to complete?

We tried generating training mazes for the UnrealEngine. From the summer project, we have 20 mazes that were generated. We managed to generate each maze. However, this is a manual process, and we aim to finish generating all the unreal mazes in the next few days. 

- What issues have you encountered?

There is not a way to programmatically generate UnrealEngine mazes. We are still new to Unreal, so we are trying to learn about maze generation using UnrealEngine. 

- I’ll also ask you to let me know the grade your group is aiming for (you’ll enter this on gradescope).

We are aiming to get an A on this project. 

# Methods Outline

## Simulation

- Discuss the creation of the different mazes in Unreal Engine. Discuss more the details of the world and the choices that were made. Explain how we use UnrealCV to control the simulation, and extract images from it.

## Data Collection

- We will collect images from the robot traversing through 5 different mazes, for an approximate total of 10,000 images. Here, we discuss the “wandering” method of the robot in its path through the maze to collect these images, and how that path is determined.

## Training

- From previous research, we found that XResNeXt18, XResNeXt50, AlexNet, DenseNet121 performed the best in the raycasting-simulation. Thus, we will train unreal engine images on these neural network architectures.

## Testing

- Here we test the different Unreal models in the Unreal simulation, as well as the raycasting models. This is the “crossing” part of the project.
Moreover, we will test the Unreal models in the raycasting-simulation to demonstrate cross-domain performance.

# Discussion Outline

- What data you will present?

We will present the 10,000+ images we collected using the automator in the Unreal mazes. As well as tables and charts to show statistics of how well the model performed navigating a maze. 

- How you will interpret/evaluate your data?

The dataset will be used to train a CNN model. We will then evaluate this model in the Unreal Engine and Raycasting simulation. 

- How your work compare to others?

Our work will be implemented in other domains. As such, we can evaluate our model's performance and compare it to other models made for the raycasting simulation. Our model is different from many others because we are using simulated data instead of images collected from real environments.

- How will you prove your point (support your claims)?

We hypothesize that cross domain adaptation is a feasible learning method. To prove this, we will run the model trained in the Unreal engine in the raycasting simulation. Conversely, models trained in the raycasting simulation will run in the Unreal mazes. If the Unreal models perform better in the raycasting simulation than raycast models in Unreal, then this indicates improvement in cross domain adaptation. 
