# FashionMNIST Based on CNN

> Name: JIN, Bowen
>
> Student Number: 20796057

```toc 
	style:
	
```
## 1. Abstract

In this project, I will study how different design choices affect the performance of a cnn network, using [FashionMNIST](https://github.com/zalandoresearch/fashion-mnist) dataset. In total, there are 4 design discussed in this report:

- preprocessing
-  overfitting problem
-  adjusting learning rate
- model complexity

 I set up 4 slightly different CNN network, they all use ReLU activation, cross entropy loss and SGD with momentum optimizer. Here is the 4 slightly different CNN network I used in this report:

- `CNN0.1` : Shallow network
- `CNN0.2` : Shallow network, Preprocessing
- `CNN0.3` : Shallow network, Preprocessing, Learning rate decay
- `CNN0.4` : Deep network, Preprocessing, Learning rate decay

I use pytorch to train the model, and tensorboard to achieve visualization. All the codes are writed on my own, and already uploaded on CANVAS. You can also see this project in my [Github](https://github.com/Bennie13/FashionMNIST-pytorch).

##  2. FashionMNIST Dataset

FashionMNIST contains 70,000 article images of [Zalando](https://jobs.zalando.com/tech/), 60,000 training samples and 10,000 stesing samples. Every sample is consisted of a **28x28 gray scale image** and one **label from 10 classes**. FashionMNIST is designed to replace the original MNIST datasets  in order to benchmark ML algorithms, so the only difference between the two datasets in the content of the grayscale image, particularly, the image content of FashionMNIST is more sophisticated to better adapt the modern CV tasks.

### 2.1 Separate the dataset

Although the dataset is already provided in the form of training and testing set, I want to make a validation set to better monitor the hyperparameters. So I further divide the training set into two parts locally, one is new training set which contains 50,000 samples, another is validation part which contains 10,000 samples. Here is a table about how I separate the data.

|                  | **Local**  | **Official** |
| ---------------- | ---------- | ------------ |
| **Training Set** | **50,000** | **60,000**   |
| **Validation**   | **10,000** | **0**        |
| **Testing**      | **10,000** | **10,000**   |

### 2.2 Create datasets locally

The datasets provided by official source is in form of bytecode. In this project, I transfered the images into `.JPG` and corresponding `.txt` file which contains the name of `JPEG` file and its label information. Each part is stored separately in corresponding directory. 

- Here is a tree view of the directory

  ```
  .
  ├── train
  │   ├── train.txt
  │   ├── 0.jpg
  │   ├── 1.jpg
  │   ├── 2.jpg
  │   ├── .
  │   ├── .
  │   ├── 49999.jpg
  ├── validation
  │   ├── validation.txt
  │   ├── 50000.jpg
  │   ├── 50001.jpg
  │   ├── 50002.jpg
  │   ├── .
  │   ├── .
  │   ├── 59999.jpg
  ├── test	
  │   ├── test.txt
  │   ├── 60000.jpg
  │   ├── 60001.jpg
  │   ├── 60002.jpg
  │   ├── .
  │   ├── .
  │   ├── 69999.jpg
  ```

- Here is a example of the `.txt`  file

  ```
  0.jpg 9
  1.jpg 0
  2.jpg 0
  3.jpg 3
  4.jpg 0
  5.jpg 2
  6.jpg 7
  7.jpg 2
  8.jpg 5
  9.jpg 5
  10.jpg 0
  .
  .
  ```



## 3. Design Choices

In this project, I implemented a CNN to solve the image classification problem. In order to further study how the different design choices affect the performance sepretively, I initially construct a very simple CNN-`CNNv0.1` which contains 2 convlutional layer with ReLU activation&maxpool and 2 fully connected layer , and I choose the cross entropy loss and SGD optimizer to train the model without any preprosessing and data augmentation. 

### 3.1 Preprocessing

#### 3.1.1 Rescaling and normalization

From the overall distribution of the input data, the input data must be normalized before training begins. The fundamental reason is that the learning process of neural network is essentially the learning of data distribution. Once the distribution of training data and test data is different, the generalization ability of the network is also greatly reduced, on the other hand, once the distribution of each batch of training data is different (batch gradient descent), then the network has to learn to adapt to the different distributions In each iteration, this will greatly slow down the training speed of the network, which is why we need to normalize the input data.

- In `CNNv0.1`, I only use `torchvision.transforms.ToTensor()` to rescale the data from `[0, 255]` to `[0, 1]`. 
- In order to study the effects, I further construct `CNNv0.2` using `torchvision.transforms.ToTensor()` and  `torchvision.transforms.Normalize((0.2869,), (0.3524,))` to achieve normalization of the whole dataset, where `0.2869` is the mean and `0.3524` is standard deviation

#### 3.1.2 Data augmentation

In deep learning, the number of samples is generally required to be sufficient. The larger the number of samples, the better the effect of the trained model and the stronger the generalization ability of the model. However, in practice, the sample size is insufficient or the sample quality is not good enough, which requires data enhancement of the sample to improve the sample quality. Data augmentation can not only increase the amount of training data and improve the generalization ability of the model, but also increase the noise data and improve the robustness of the model.

- In `CNNv0.1`, I do not use any data augmentation 
- In `CNNv0.2`, I use `torchvision.transforms.RandomHorizontalFlip()` and `torchvision.transforms.RandomCrop(28, padding=2)` to implement data augmentation.

#### 3.1.3 Performance

|                                   | **Test loss** | **Test accuracy** |
| --------------------------------- | ------------- | ----------------- |
| **`CNNv0.1(no preprocessing)`**   | **0.2792**    | **90.53%**        |
| **`CNNv0.2(with preprocessing)`** | **0.2288**    | **91.85%**        |

Data preprocessing do enhance the performance of the network as expected.



### 3.2 Overfitting

#### 3.2.1 Introduction

Overfitting is when the gap between training error and test error is too large. In other words, the complexity of the model is higher than the real problem, and the model performs well on the training set but poorly on the test set. The model can remember the attributes or features of the training set that are not suitable for the test set, does not understand the laws behind the data, and has poor generalization ability. In general, there are 3 reasons for overfitting:

- The training data set has a single sample and insufficient samples. If the training samples only have negative samples, then the generated model predicts positive samples, which is definitely not accurate. Therefore, the training samples should be as comprehensive as possible, covering all data types.
- Too much noise in the training data. Noise refers to interfering data in the training data. Too much interference will result in the recording of many noisy features, ignoring the relationship between the real input and output.
- Model is too complex. The model is too complex, and it has been able to "rotate" the information of the training data, but it cannot be adapted when encountering unseen data, and the generalization ability is not efficient. We have to make the model have stable output for different models. Models that are too complex are an important factor in overfitting.

#### 3.2.2 Experiment

During the training process of `CNNv0.1`, here is a overfitting situation as showed below: 

<img src="https://raw.githubusercontent.com/Bennie13/Notes-Images/main/Images/202205082048640.png" style="width:50%;"/><img src="https://raw.githubusercontent.com/Bennie13/Notes-Images/main/Images/202205082048917.png" style="width:50%;"/>
<center style="color:#C0C0C0;text-decoration:underline">CNNv0.1: training loss(left) and validation loss(right) </center>
Comparing the two graphs, the training loss continues to decrease during the training time, while the validation loss decreases fast initially and begins to rebound after 40 epochs. Obviously, this is a overfitting problem.

#### 3.2.3 Solution

In order to solve the overfitting problem, I implemented  preprocessing procedures as discussed before to create more different samples further to expand the dataset. Here is the loss graph of `CNNv0.2`:

<img src="https://raw.githubusercontent.com/Bennie13/Notes-Images/main/Images/202205082052211.png" style="width:50%;"/><img src="https://raw.githubusercontent.com/Bennie13/Notes-Images/main/Images/202205082052637.png" style="width:50%;"/>
<center style="color:#C0C0C0;text-decoration:underline">CNNv0.2: training loss(left) and validation loss(right) </center>
Comparing the two graphs, they both decrease during training time and the validation loss does not rebound as the situation in `CNNv0.1`.  The overfitting problem is solved. Further, if we want train more epochs to make the model better, we will encounter overfitting problem, because the number of data is finite, there will be a certain time that the model can “learn” all the data just well. After that moment, overfitting shows up. So we need to design our datasets, model, training scheme properly.



### 3.3 Learning rate decay

#### 3.3.1 Introduction

When training a neural network, use the learning rate to adjust the speed of parameter updates. When the learning rate is small, the update speed of the parameters will be greatly reduced. When the learning rate is large, the search process oscillates, causing the parameters to hover around the optimal value. I noticed this when training `CNNv0.2`. To this end, a learning rate decay is introduced in the training process, so that the learning rate gradually decays as the training progresses.

- In `CNNv0.2`, SGD optimizer is used, and there is no learning rate decay strategy
- In `CNNv0.3`, I added a scheduler `optim.lr_scheduler.MultiStepLR(optimizer, milestones=[60, 80], gamma=0.1)`. The scheduler will make a 10-fold decrease of the present learning rate when the number of epoch reaching 60 and 80. Because when I trained `CNNv0.2`, I noticed the validation loss is fluctuating after epoch 60.

#### 3.3.2 Performance
<img src="https://raw.githubusercontent.com/Bennie13/Notes-Images/main/Images/202205082053732.png" style="width:50%;"/><img src="https://raw.githubusercontent.com/Bennie13/Notes-Images/main/Images/202205082053516.png" style="width:50%;"/>
<center style="color:#C0C0C0;text-decoration:underline">validation loss in CNNv0.2(left) and CNNv0.3(right)</center>

From the two graphs, there is a obvious decrease after adjusting the learning rate at 60 epochs and the curve is suddenly becoming more smoother than `CNNv0.2`. In `CNNv0.2`,  the validation loss begins to fluctuate around 0.23 after 60 epochs. While in `CNNv0.3`, smaller learning rate further enhance the performance of the model with validation loss at 0.21 eventually.

|                                         | **Test loss** | **Test accuracy** |
| --------------------------------------- | ------------- | ----------------- |
| **`CNNv0.2(no leaning rate decay)`**    | **0.2288**    | **91.85%**        |
| **`CNNv0.3(with learning rate decay)`** | **0.2205**    | **92.17%**        |

Design a proper strategy of learning rate decay do increase the peroformance of the model as expected.



### 3.4 Model complexity

Bengio and LeCun's 2017 article ^[1] has this sentence: "We argue that most functions that can be compactly represented by deep architectures cannot be represented by compact shallow architectures." This might mean , if most functions can solve this problem with a deep structure a, it is impossible to solve it with a shallower, equally compact structure. To solve more complex problems, either increase the depth or increase the width, and the cost of increasing the width is often much higher than the cost of increasing the depth.

#### 3.4.1 Advantages and drawbacks

The main modules of the current deep learning network structure are convolution, pooling and activation. Activation is a standard nonlinear transformation module. A deeper model means better nonlinear representation ability, can learn more complex transformations, and thus can adapt to more complex feature inputs. But this does not mean that the deeper the better, the deepening of the model brings two problems:

-  The optimization problem brought about by the deepening. The gradient caused by the deep network is unstable, and the problem of network degradation always exists, which can be alleviated but cannot be eliminated. This may cause the network to deepen, and the performance will start to decline. 
-  The saturation brought by the deepening of the network. As the depth increases, the lifting effect of the model gradually saturates. In addition, some problems that may occur with model deepening are that the learning ability of some shallow layers is reduced, which limits the learning of deep networks, which is also a very important factor for structures such as skip connections to play a role.

#### 3.4.2 Experiment

- In `CNNv0.3`, I use `conv layer + pooling layer` as a block. In total, there 2 blocks and eventually connected to 2 FC layer.(input is blue, conv is green, pooling is yellow, red is fully connected)
![](https://raw.githubusercontent.com/Bennie13/Notes-Images/main/Images/202205082116545.png)
- In `CNNv0.4`, I take `VGG` network as reference, which is designed to prove that increasing the depth of the network can affect the final performance of the network to a certain extent. I only use the first 2 stages of `VGG`, I use ` 2 conv layer + batchnorm + pooling layer` as a block. In total, there 2 blocks and eventually connected to 2 FC layer
![](https://raw.githubusercontent.com/Bennie13/Notes-Images/main/Images/202205082116580.png)


#### 3.4.3 Performance
<img src="https://raw.githubusercontent.com/Bennie13/Notes-Images/main/Images/202205082054369.png" style="width:50%;"/><img src="https://raw.githubusercontent.com/Bennie13/Notes-Images/main/Images/202205082054689.png" style="width:50%;"/>
<center style="color:#C0C0C0;text-decoration:underline">validation loss in CNNv0.2(left) and CNNv0.3(right)</center>

<center style="color:#C0C0C0;text-decoration:underline">validation loss in CNNv0.3(left) and CNNv0.4(right)</center>

|                                 | Test Loss  | Test Accuracy |
| ------------------------------- | ---------- | ------------- |
| **`CNNv0.3 (shallow network)`** | **0.2205** | **92.17%**    |
| **`CNNv0.4 (deep network)`**    | **0.1844** | **94.47%**    |

We need to match the right model complexity according to the data complexity to get best performance. Under this circumstances, a deep network do improves the performance of the model a lot.



## 4.Reference

1. Bengio Y, LeCun Y. Scaling learning algorithms towards AI[J]. Large-scale kernel machines, 2007, 34(5): 1-41.
1. [H Xiao](https://scholar.google.com/citations?user=jp7swwIAAAAJ&hl=en&oi=sra), [K Rasul](https://scholar.google.com/citations?user=cfIrwmAAAAAJ&hl=en&oi=sra), [R Vollgraf](https://scholar.google.com/citations?user=w8qPxSUAAAAJ&hl=en&oi=sra) - arXiv preprint arXiv:1708.07747, 2017 - arxiv.org
1. The MIT License (MIT) Copyright © [2017] Zalando SE, [https://tech.zalando.com](https://tech.zalando.com/)
