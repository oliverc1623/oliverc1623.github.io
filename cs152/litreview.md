# Literature Review

## [**Driving Policy Transfer via Modularity and Abstraction**](https://arxiv.org/pdf/1804.09364.pdf)

This paper aims to bridge the reality gap through modularity and abstraction. Paper used CARLA, which is an open-source urban driving simulator. The paper implemented an encoder-decoder CNN with a perception system. This perception system takes in images from a camera but segments the image into "road" and "non-road" components.

## [**Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks**](https://openaccess.thecvf.com/content_ICCV_2017/papers/Zhu_Unpaired_Image-To-Image_Translation_ICCV_2017_paper.pdf)

Unpaid image-to-image translation converts an image from one representation to another. This paper implemented this technique with a cycle generative adversarial network. This network includes a loss function that uses cycle consistency loss. The researchers found positive results when translating colors and texture. However, they note that geometric changes found little success.

## [**UnrealCV: Connecting Computer Vision to Unreal Engine**](https://link.springer.com/content/pdf/10.1007/978-3-319-49409-8_75.pdf)

Computer graphics can construct virtual worlds that allow different agents to simulate interactions in different environments. This group uses Unreal Engine 4 to construct a tool, UnrealCV, that allows researchers to construct virtual worlds and connect a neural network to an agent in a world, allowing the network to train from the simulated data and direct the agent.

## [**RoboTHOR: An Open Simulation-to-Real Embodied AI Platform**](https://arxiv.org/abs/2004.06799)

This paper introduces RoboTHOR, a platform that helps develop and train agents on various AI navigation tasks in simulated environments and enables testing in both the simulation and the real world. The paper discusses the many challenges associated with the nature of transferring learning between real and simulated worlds. As a platform, RoboTHOR aims to overcome these many challenges by providing an accessible and replicable system that focuses on the learning between simulated spaces and its corresponding physical environment. Initial experimentation has shown that there still is a large gap to overcome, but they hope RoboTHOR will narrow the gap as it’s continually used and updated.