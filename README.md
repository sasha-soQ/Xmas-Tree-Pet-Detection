# Xmas-Tree-Pet-Detection
Deep Learning Project
Abstract
Nowadays, people keep pets as children. However, sometimes
pets can be mischievous, vandalizing people’s properties.
In this project, I fine-tuned a transfer learning model
based on YOLOv7 to do object detection, distinguishing the
pets and the properties, Xmas tree in this case, and notify
owners once their pets stay around the Xmas tree for too
![night](https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/2f13e0a5-a33d-40de-b012-14c28350e55e)

long.
1. Introduction
Videos about pets destroying Xmas trees are trending
when it comes to Christmas every year. Although the viewers
might find it cute and funny, as a pet owner, I have to say
it is really tiring. The reason why I chose this topic for my
final project is to keep my pets away from the Xmas tree.
With the help of object detection, whenever our fur babies
approach or even attack the tree, we will receive a notification
and take action before anything terrible happens. After
all, saving our Xmas tree and decorations is saving us
money.
2. Data
The dataset is a series of labeled image sequences converted
from videos captured by the security camera in my
living room. I labeled 496 images with LabelImg as training
data and the YOLOv7 tool does augmentation automatically,
as shown in Figure 2.
Figure 1. Labeling with LabelImg and labeled dataset
