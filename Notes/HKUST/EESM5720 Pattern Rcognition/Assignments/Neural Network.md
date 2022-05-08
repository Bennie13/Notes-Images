```python
import numpy as np

num_input = int(input("请输入D="))
num_hidden = int(input("请输入M="))
num_output = int(input("请输入K="))
# hidden_act = input("请输入隐藏层激活函数类型：")
output_act = int(input("请输入输出层激活函数类型：1.softmax  2.linear"))

def relu(x):
    y = np.zeros(x.shape)
    for i in range(len(x)):
        if x[i] <= 0:
            y[i] = 0
        else:
            y[i] = x[i]
    return y

def softmax(x):
    return np.exp(x)/sum(np.exp(x))

x = np.zeros(num_input)
matrix1 = np.zeros((num_hidden,num_input+1), dtype = np.float)
matrix2 = np.zeros((num_output,num_hidden+1), dtype = np.float)

for i in range(len(x)):
    num = float(input("请输入x的值，一次一个"))
    x[i] = num

if output_act == 1:
    for i in range(len(matrix1)):
        for j in range(len(matrix1[0])):
            num = float(input("1请按题目顺序输入第一层计算的系数一次一个"))
            matrix1[i][j] = num

    for i in range(len(matrix2)):
        for j in range(len(matrix2[0])):
            num = float(input("2请按题目顺序输入第一层计算的系数一次一个"))
            matrix2[i][j] = num

    x = np.insert(x, 0, 1.0)
    z = matrix1.dot(x)
    z = relu(z)
    print("\nHidden Layer: ",z)

    y = matrix2.dot(np.insert(z, 0, 1.0))
    y = softmax(y)
    print("Output Layer: ",y)

elif output_act == 2:
    for i in range(len(matrix2)):
        for j in range(len(matrix2[0])):
            num = float(input("2请按题目顺序输入第一层计算的系数一次一个"))
            matrix2[i][j] = num

    z = np.zeros(num_hidden)
    for i in range(len(z)):
        num = float(input("请输入隐藏层输出："))
        z[i] = num
    y = matrix2.dot(np.insert(z, 0, 1.0))
    print("Output Layer: ", y)

    t = np.zeros(num_output)
    for i in range(len(t)):
        num = float(input("请输入期望输出："))
        t[i] = num
    error = y - t
    print("Output error:", error)

    err_matrix2 = error.reshape(error.shape[0], 1) * z
    print("上标为2的derivative of the error function：\n", err_matrix2)

    err_matrix1 = np.delete(np.transpose(matrix2),0,0).dot(error.reshape(error.shape[0],1))
    err_matrix1 = err_matrix1.reshape(1,err_matrix1.shape[0]) * x
    print("上标为1的derivative of the error function：\n", err_matrix1)

```

# Problem 1

Consider the multi-layer feedforward neural network shown below:

![nn_bishop.jpg](https://canvas.ust.hk/assessment_questions/304680/files/4629164/download?verifier=m9WqEFls5POnboVoqvlFFeN3Jbt85AwMdJM8fIw6) 

The hidden layer and output layer neurons have outputs given by $z_j=h(\sum_{i=0}^{D}{\omega_{ji}^{(1)}x_i})$ and $y_k=h(\sum_{i=0}^{M}{\omega_{kj}^{(2)}z_j})$.

Assume the network has D = 2 inputs, M = 3 hidden units and K = 2 outputs. The bias units have constant values  x0 = z0 = 1 . Assume that the activation functions in the hidden layer are ReLu functions and that the activation functions in the output layer are given by the soft-max function.

Suppose that the weights are given by

w10(1)= -0.4, w11(1)= -1.4, w12(1)= -1.5

w20(1)= 1, w21(1)= -0.3, w22(1)= 0.3

w30(1)= -0.2, w31(1)= 0.3, w32(1)= 0.1

w10(2)= -0.1, w11(2)= -0.1, w12(2)= 0.9, w13(2)= 1.9

w20(2)= -1.5, w21(2)= 1.7, w22(2)= -0.8, w23(2)=  -0.4

Suppose that the input to this network is given by x1= 0 and x2= -0.4

Give the output of the second hidden layer neuron to two decimal places.

***Ans:*** 0.88

# Problem 2

Consider the multi-layer feedforward neural network shown below:

![nn_bishop.jpg](https://canvas.ust.hk/assessment_questions/304680/files/4629164/download?verifier=m9WqEFls5POnboVoqvlFFeN3Jbt85AwMdJM8fIw6) 

The hidden layer and output layer neurons have outputs given by $z_j=h(\sum_{i=0}^{D}{\omega_{ji}^{(1)}x_i})$ and $y_k=h(\sum_{i=0}^{M}{\omega_{kj}^{(2)}z_j})$ .

Assume the network has D = 2 inputs, M = 2 hidden units and K = 2 outputs. The bias units have constant values  x0 = z0 = 1 . Assume that the activation functions in the hidden layer are ReLu functions and that the activation functions in the output layer are linear.

Suppose that the second layer weights are given by

w10(2)= -1.1, w11(2)= -0.2, w12(2)= 0.3

w20(2)= 1.4, w21(2)= -1, w22(2)= -1.2

Suppose that in response to the input x1= -1.7 and x2= -1.1, the hidden layer outputs are z1=  0.6 and z2=  0.2. The desired outputs are t1= 0.3 and t2= -0.1.

Suppose we wish to minimize the squared error cost function, $E=\frac{1}{2}\sum_{k=1}^{K}{y_k-t_k}^2$

Find the derivative of the error function with respect to the weight w12(2) to two decimal places.

***Ans:*** -0.29 