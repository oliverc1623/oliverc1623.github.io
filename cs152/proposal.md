# Crossing the Reality Gap

Over the summer, I investigated multiple neural network (NN) architectures for autonomous navigation in simulation. We used a render from the Raycast module to make custom mazes for models to traverse. The raycasting simulation renders a maze with a an arrow to direct the agent and a blue box, indicating the end. 

![](/images/learner.gif)

In this project, I will take the best architecture from that survey to train a more robust model that will work well the real world. To cross this reality gap, I need to train a model in a realistic looking simulation using the Unreal Engine. 

For data collection, I'll build an automator to collect images of the maze with proper camera orientation. The automator can include two variations to data collection such as uniformly placing the bot and wandering through the maze with random noise. After making the dataset, the next step would apply technique called CycleGAN, which is image-to-image translation. This process will also require training a neural network. Ideally, an well-trained model should traverse the maze with 100% accuracy over many mazes with multiple repetition. The end goal would be to apply our best model to a real-life robot, which could involve some electronics work. 

![](/images/map.png)

# Goals

1. Examine a raycast trained model perform in an Unreal simulation

2. Exmaine an Unreal trained model perform in a raycast simulation

3. Compare results on different image-to-image translations

4. Apply best model to robot in real life