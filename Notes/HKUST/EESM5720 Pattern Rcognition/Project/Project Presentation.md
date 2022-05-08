# PAGE1 FashionMNIST based on CNN

Good evening. This is JIN, Bowen. The topic of my project is FashionMNIST based on CNN

# PAGE 2 FashionMNIST

First, Lets take a look at the datasets.

FashionMNIST contains 70,000 article images of [Zalando](https://jobs.zalando.com/tech/), 60,000 samples for training and 10,000 samples for testing. Each sample is consisted of a **28x28 grayscale image** and a **label from 10 classes**. ~~FashionMNIST is designed to replace the original MNIST datasets  in order to benchmark ML algorithms, so the only difference between the two datasets in the content of the grayscale image, particularly, the image content of FashionMNIST is more sophisticated to better adapt the modern computer vision tasks.~~

Because I want a validation set to better train the model, so I further separate it.

# PAGE 3 Separate FashinMNIST

- the dataset provided by pytorch is in the form of bytecode, I transfer it to jpeg and generate correspnding txt file to store label information
- In this project, there are 50,000 samples for training, 10,000 samples for validate, 10,000 samples for testing. You can see right-hand side is the local file structure of the dataset and example of txt file

# PAGE 4 CNNv1

In total, I trained 4 different CNN in this project. Now, lets look at the first one

- here is a network structure below. Blue is input. Azure is convolutional layer. Yellow is pooling layer. red is fully connected layer. At beginning, I just build this simple network
- on the left-hand side is some properties of the network you can see. In CNNv1, there is no data preprocessing but only rescale to  [0,1]
- we can see the training loss here is going down all the way to 0, while validation loss begins to rebound after 40 epochs. So its   a overfitting. and I save the best model during traing, got about 90% accuracy. 
- I don't want to make tradeoff between training time and overfitting, so I do a data augmentation to study whether it can solve the problem and also better the performance

# PAGE 5 CNNv2

So I implement random Horizontal flip and random crop to expand the datasets, making it harder to be learned. Also I calculate the mean and standard deviation to normalize the whole dataset.

- Here we can see the top left picture is training loss curve of CNNv2, it is more fluctuating comparing the below CNNv1 , this means the data becomes harder to be learned.
- and the top right picture is validation loss of CNNv2, the overfitting problem is solved. the validation loss do not rebound .and the test accuracy is also increased by 1.32% which means better performance. 

# PAGE 6 CNNv3

I noticed that after 60 epochs, the validation loss stop to decrease but linger around.

-  so I guess it may be linger around the optimal point due to the large learning rate. so I implement a learning rate decay

- At 60 epoch, I decreased the learning rate by 10 times. we can see after the leaning rate decreased, there is a fast decreasing on the curve, and the curve is also getting smooth. And the test accuracy is increased by 0.59%.

# PAGE 7 CNNv4

At last, I build a deeper network than before. this is a network structure, I referenced the VGG network, added two more convlutional layer,also increased the filter number, you can see the blocks are widder a lot than before

- we can see from the picture the performace is inreased a lot, test accuracy inreased by 2.2%

-  A deeper model means better nonlinear expression ability, can learn more complex transformations, and thus can fit more complex feature inputs. But it does not mean the deeper the better, there also are many problems coming with it. So we need to match the right model complexity according to the data complexity to get best performance.

# PAGE 8 

This is the end of my presentation.Thank you for your paticient listening! 