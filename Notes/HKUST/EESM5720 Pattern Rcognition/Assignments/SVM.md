# Problem 1 

Suppose that we use an SVM with a linear kernel and slack variables to classify the data shown below. Each point is labelled with its index n.  Target labels tn -1 (red) and +1 (blue). 

![svm_avalues_3.png](https://canvas.ust.hk/assessment_questions/304798/files/4637171/download?verifier=3aojQriu9IXZoNL9duzTL1GMBLCMI2cGQn0JXeE9)

Classification decisions are made by comparing a discriminant function

y(x)=∑n=1Nank(xn,x) 

to zero. The bias is zero. 

The box constraint parameter was C=0.2 . The Lagrange Multipliers an obtained by training on the data are shown in the table below.

| n    | 0    | 1    | 2    | 3    | 4    | 5    | 6    | 7     | 8    | 9     |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ----- | ---- | ----- |
| an   | 0    | 0    | -0.2 | 0.2  | 0    | 0.2  | 0    | -0.15 | -0.2 | -0.15 |

For each of the data points, indicate whether it lies inside the margin, outside the margin or on the margin.

Point 0:      outside

Point 1:      outside 

Point 2:      inside

Point 3:      inside

Point 4:      outside

Point 5:      inside

Point 6:      outside

Point 7:      on

Point 8:      inside

Point 9:      on

# Problem 2

Suppose that we use an SVM with a linear kernel and slack variables to classify the data shown below. Each point is labelled with its index n.  Target labels tn -1 (red) and +1 (blue). 

![svm_boundary_4.png](https://canvas.ust.hk/assessment_questions/304825/files/4637556/download?verifier=ha0j4YGMKbLCipUyd747RAnB0eICUNkCV2xQbJcJ)    

Classification decisions are made by comparing a discriminant function

y(x)=∑n=1Nank(xn,x) 

to zero. The bias is zero. If x=[x1x2]T, the discriminant function can also be written as

y(x)=w1x1+w2x2

Training the SVM with the box constraint parameter C=0.2, we find the following support vectors and coefficients an. 

The support vector (-1.9,0.4) has coefficient -0.16.
The support vector (0.8,1.2) has coefficient -0.2.
The support vector (-0.6,-1.4) has coefficient -0.2.
The support vector (1.9,-0.4) has coefficient 0.16.
The support vector (-0.2,1.4) has coefficient 0.2.
The support vector (-0.1,-1.5) has coefficient 0.2.

Give the values of w1 and w2 to two decimal places.

w1= 0.51

w2= -0.11

# Problem 3

The two plots below show the training data, decision regions (blue areas are classified as class 0 and red areas as class 1) and support vectors (circled in green) of two support vector machine classifiers with linear kernels.

The two plots differ in the value of the regularization parameter C chosen. Which plot corresponds to the smaller value of C?

![svm_vary_C_5.png](https://canvas.ust.hk/assessment_questions/304772/files/4636098/download?verifier=HPWrxIi73ULgs9fZeclhuiax9vo5XdL3Le8jQosj)     

 

***Ans:*** Plot B



 