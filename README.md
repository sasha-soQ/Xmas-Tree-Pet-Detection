# Xmas-Tree-Pet-Detection
### Deep Learning Project

<figure class="a">
<img src=https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/2f13e0a5-a33d-40de-b012-14c28350e55e width=60% />&emsp; <img src=https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/157bcc2d-60be-45b8-97e0-511cea6b7ef2 width=20% />
</figure>

<video width="600" height="360" src="https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/fa726546-7945-4293-8980-cc20fbfd6b92"></video>

### Abstract
Nowadays, people keep pets as children. However, sometimes pets can be mischievous, vandalizing people’s properties. In this project, I fine-tuned a transfer learning model based on YOLOv7 to do object detection, distinguishing the pets and the properties, Xmas tree in this case, and notify owners once their pets stay around the Xmas tree for too long.

## 1. Introduction
Videos about pets destroying Xmas trees are trending when it comes to Christmas every year. Although the viewers might find it cute and funny, as a pet owner, I have to say it is really tiring. The reason why I chose this topic for my final project is to keep my pets away from the Xmas tree. With the help of object detection, whenever our fur babies approach or even attack the tree, we will receive a notification and take action before anything terrible happens. After all, saving our Xmas tree and decorations is saving us money.

## 2. Data
The dataset is a series of labeled image sequences converted from videos captured by the security camera in my living room. I labeled 496 images with LabelImg as training data and the YOLOv7 tool does augmentation automatically, as shown in Figure 2.

<figure class="a">
<img src=https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/5d2b4e72-735e-4948-a99d-b88dafd61c03 width=40% /><img src=https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/95f5c787-d177-40ee-ba37-4068c34a8b01 width=40% />
</figure>  

*Figure 1. Labeling with LabelImg and labeled dataset*  

<figure class="a">
<img src=https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/4dc52210-d9be-4d63-b037-e6634a3c57b9 width=15% /><img src=https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/03ba6b73-c309-4dcc-a7a0-ddbe14f7825b width=15% />
</figure>

*Figure 2. YOLOv7 Augmentation*

## 3. Methods
The method applied in this project is transfer learning based on YOLOv7, with fine-tuning using a customized dataset. I’ve considered using the original pre-trained model YOLOv7 along with open-source Coco dataset images including cat and dog labels, but the result shows low accuracy and confidence, as shown in Figure 3.

<figure class="a">
<img src=https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/6e36e37c-7642-4397-b5ad-91082ff8186c width=25% /><img src=https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/954f06a1-7e1d-4dd8-99df-d0f8451685b6 width=25% />
</figure>

*Figure 3. Comparison of pre-trained YOLOv7 with Coco dataset weight and after fine-tuning with both conf-threshold and iou-threshold is 0.3*

## 4. Experiments
In this project, I use an Android emulator to stream the security camera filming the Xmas tree. Next, capture every single frame and determine whether any cat or dog has come across the scene and overlaps with the Xmas tree. If a dog, a cat, or both a dog and a cat approach the tree for more than 40 frames within 50 frames. It will trigger the Line notify bot to send a message along with a labeled image to inform owners, “Your dog/cat is being naughty!”. The time interval between two Line notifications will be no less than 1 minute.

The outcomes with different confidence thresholds of my model are shown in Figure 4. Figure 5 includes a comparison of day and night conditions, with different natural lights and indoor lights, which shows the model works efficiently in different environments. The F1 score is shown in Figure 6. When the confidence falls between 0.9-0.95, we get the F1 score of 1. Therefore, the confidence threshold is set to 0.9 in this case and the result came out fairly accurate from practical observation without misjudgment. Figure 7, respectively shows the loss of bounding boxes, objects, and classes.

<figure class="a">
<img src=https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/61875d51-df23-4add-8a4b-69a7e4827f07 width=35% /><img src=https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/b10e353c-4bd9-40a6-bb43-e9d4eb1595f1 width=35% />
</figure>

*Figure 4. Comparison of 0.003 confidence threshold and 0.7 confidence threshold of my model*

<figure class="a">
<img src=https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/5d2de558-d7ce-4e1c-95e4-386b8714e8ae7 width=35% /><img src=https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/3edb1075-9c51-47c2-907e-361060fb5b5c width=35% />
</figure>
  
*Figure 5. Comparison of day and night conditions with different natural lights and indoor lights*

<img src=https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/4da63139-7139-41f0-a05b-1c5e68b76a487 width=35% />

*Figure 6. F1 curve*

<img src=https://github.com/sasha-soQ/Xmas-Tree-Pet-Detection/assets/109583554/6c5b3c17-6dff-490e-b8f9-c261721ad4a2 width=35% />

*Figure 7. Loss*

The common failure modes of my model would be when pets go behind and are blocked by the Xmas tree. In this case, pets are not detected and thus failed to inform owners.

## 5. Conclusion
In conclusion, the Xmas tree is rescued. To make it more functional, my ideas for future extensions are:

1) Buy a better security camera, and connect it to edge devices coordinate with sirens. So, whenever pets go near Xmas tree, the alarm will go off and keep them away immediately.
2) Probably combine the model with RNN to eliminate the pet-behind-tree hazard.
