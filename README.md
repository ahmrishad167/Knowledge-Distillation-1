# Knowledge-Distillation

## A Simple Implementation of [Distilling the Knowledge in a Neural Network](https://arxiv.org/pdf/1503.02531.pdf) (NIPS, 2014) using PyTorch
From below, Knowledge Distillation is abbreviated as KD. </br>
VGG19 with Batch Normalization network serves as a teacher network. The dataset used is CIFAR dataset. </br>
### **The result may vary, depending on the set of hyper-parameters.**


### 1. Quantitative Evaluation
#### 1) CIFAR10
| Model | Top 1 Accuracy | Top 5 Accuracy |
|:-------------:|:-------------:|:-----:|
| Teacher (VGG19 with BN) | 84.45% | 99.22% |
| Student (w/o KD) | 67.04% | 97.11% |
| Student (with KD, Temp = 5) | 79.72% | 99.00% |
| Student (with KD, Temp = 20) | 78.41% | 98.77%|

### 2. Accuracy and Loss during Training
#### a) CIFAR10

| Model | Accuracy | Loss |
|:-----:|:-----:|:-----:|
| Teacher | <img src = './Teacher Model Accuracy.png' width=600> | <img src = './Teacher Model Loss.png'> |
| Student (w/o KD) | <img src = './Without Knowledge Distillation Accuracy.png'> | <img src = './Without Knowledge Distillation Loss.png'> |
| Student (with KD, Temp = 5) | <img src = './Knowledge Distillation Accuracy.png'> | <img src = './Knowledge Distillation Loss.png'> |
| Student (with KD, Temp = 20) | <img src = './Knowledge Distillation Accuracy.png'> | <img src = './Knowledge Distillation Loss.png'> |


### 3. Run the Code
#### 1) Train

You should have a pre-trained teacher network in order to train a student network with KD. </br>
a) Train Teacher Network. `python train.py --tto True` </br>

Then compare the performance between training the student network alone and distilling knowledge from teacher network to student network.
b) Train Student Network (without KD). `python train.py` </br>

c) Train Student Network (with KD). `python train.py --kd True --temp 5` </br>

#### 2) Evaluate
a) Evaluate Teacher Network `python test.py --tto True` </br>

b) Evaluate Student Network (without KD). `python test.py` </br>

c) Evaluate Student Network (with KD). `python test.py --kd True` </br>