# Extended MNIST Classification using Modified DenseNet

## Overview
This project focuses on developing an efficient CNN model for classifying the Extended MNIST (EMNIST) dataset. We modified the DenseNet architecture to create a lightweight model that maintains high accuracy while reducing inference time.

## Objective
- Design and train a CNN model for EMNIST classification
- Achieve optimal balance between accuracy and inference time
- Develop a more efficient model compared to baseline models (LeNet5, ResNet50)

## Development Environment
- Hardware: 4x NVIDIA A5000 24GB GPUs (Distributed Training)
- Framework: Python with modularized components
- Dataset: EMNIST Balanced dataset

## Methodology

### Dataset Selection
- Chose EMNIST Balanced dataset to prevent class imbalance issues
- Used EMNIST bymerge/byclass datasets for transfer learning
- Implemented custom dataset resizing for different model architectures

### Baseline Models
1. LeNet5
   - Test Accuracy: 86.90%
   - Training Time: 171.13s
   - Parameters: 65,104

2. ResNet50
   - Test Accuracy: 90.40%
   - Training Time: 1449.46s
   - Parameters: 23,684,015

## Development Process

### 1. Initial Model Selection
First attempted models:
- EfficientNetB1
- VGG16
- MobileNet
- ShuffleNet

Challenges faced:
- Vanishing gradient problems
- Unstable training
- Poor accuracy

### 2. Architecture Revision
Selected new candidates focusing on feature reuse:
- Wide ResNet (WRN)
- DenseNet
- Dual Path Networks (DPN)

Selected DenseNet as final base model due to:
- Efficient parameter utilization
- Simple implementation
- Effective gradient flow

### 3. Model Optimization

#### Hyperparameter Tuning
- Learning Rate: 0.001
- Optimizer: Nesterov
- Activation Function: ELU
- Batch Size: 1024
- Dropout Rate: 0.3 (at top layer)

#### Architecture Modifications
- Modified Dense Block structure (3-6-12-6 convolution layers)
- Adjusted transition layers
- Optimized input padding
- Applied transfer learning using bymerge dataset

## Results

### Final Model Specifications
- Parameters: 2,152,667
- Training Time: 1684.80s (batch size 1024)
- Top-1 Accuracy: 90.72%
- Top-5 Accuracy: 99.80%
- Evaluation Time: 5.885s
- Inference Time: 5.361s

### Performance Comparison

| Model     | Parameters  | Training Time | Test Accuracy |
|-----------|-------------|---------------|---------------|
| LeNet5    | 65,104      | 171.12s       | 86.90%       |
| ResNet50  | 23,684,015  | 1449.46s      | 90.40%       |
| Our Model | 2,152,667   | 1684.80s      | 90.72%       |

## Key Findings
- Dataset characteristics significantly influence model architecture selection
- Feature reuse mechanisms are crucial for small image classification
- Careful hyperparameter tuning can substantially impact model performance
- Transfer learning effectively improves accuracy and stability

## Future Improvements
- Further model compression techniques
- Explore alternative activation functions
- Investigate more efficient training strategies
- Additional architecture optimizations

## References
1. Cohen, G., et al. (2017). EMNIST: Extending MNIST to handwritten letters. IJCNN 2017
2. Huang, G., et al. (2017). Densely connected convolutional networks. CVPR 2017
3. [Full EMNIST Dataset on Kaggle](https://www.kaggle.com/datasets/crawford/emnist)