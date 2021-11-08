---
# These are meta-variables defined with YAML syntax, change them as you wish.
# see https://pandoc.org/MANUAL.html#variables
title: TDT4195 IP Assignment 2
author:
- Vegard Haraldstad
date: \today # This is a latex command, ignored for HTML output
lang: en-US
papersize: a4
geometry: margin=4cm
toc: false
toc-title: "List of Contents"
toc-depth: 2
numbersections: false
colorlinks: true
links-as-notes: true
# The document is following the break written using Markdown syntax
---

# Task 1

## a)

Inserting 

$$
H_2 = H_1
$$
$$
W_2 = W_1
$$
$$
F_H = F_W = 5
$$
$$
S_H = S_W = 1
$$

Into equation (1) and (2) yields

$$
P_H = P_W = 2
$$

## b)

Inserting 

$$
H_1 = W_1 = 512
$$
$$
H_2 = W_2 = 504
$$
$$
P_H = P_W = 0
$$
$$
S_H = S_W = 1
$$

Into equation (1) and (2) yields

$$
F_H = F_W = 9
$$

which gives a square kernel of odd size as the task requested.

## c)

Again, using equation (1) and (2) and inserting

$$
H_1 = W_1 = 504
$$
$$
S_H = S_W = 2
$$
$$
P_H = P_W = 0
$$
$$
F_H = F_W = 2
$$

yields

$$
H_2 \times W_2 = 252 \times 252
$$

## d)

Inserting

$$
H_1 = W_1 = 252
$$
$$
S_H = S_W = 1
$$
$$
P_H = P_W = 0
$$
$$
F_H = F_W = 3
$$

yields

$$
H_2 \times W_2 = 250 \times 250
$$


## e)

Since each layer has square kernels and a convolution operation and a maxpool operation, the number of weights, N_wi for each layer will be

$$
N_{w i} = (F_{conv i}^2 + F_{m pool i}^2) * C_{i-1} * C{i}
$$

For the different layers we get

$$
N_{w 1} = 928 800
$$
$$
N_{w 2} = 26624 18432
$$
$$
N_{w 3} = 106496 73728
$$

Further the number of biases will equal the number of output filters.

$$
N_{b 1} = 32 
$$
$$
N_{b 2} = 64 
$$
$$
N_{b 3} = 128
$$

For the NN we have

$$
N_{w4} = (4*4)*128*64 = 131072   
$$

$$
N_{b4} = 64   
$$

$$
N_{w5} = 64*10 = 640   
$$

$$
N_{b5} = 10   
$$

Summing up the number of parameters we have

$$
N_p = 224970
$$




## f)

Using zero padding, the convolution produces the following image

![](images/Task_1_f.PNG){height=10em}

\clearpage


# Task 2

## a)

An image of a lake in grayscale

![](images\lake_greyscale.jpg){height=25em}

## b)

An image if a lake in grayscale inverted

![](images\lake_greyscale_inverse.jpg){height=25em}

## c)

An convoluted image of a lake, using the kernel h_a

![](images\im_sobel.jpg){height=25em}

An convoluted image of a lake, using the kernel h_b

![](images\im_smoothed.jpg){height=25em}

\clearpage

# Task 3

## a)

XOR is a boolean operator that can't be represented by a single-layer neural network. Given a network with two inputs, two weights, one bias and one output, it is not possible to choose the weights and bias in such a way that we can achieve both the or operation when only one of the inputs is active, and in the same time get the exclusivity when both inputs are active on the same time.

## b)

A hyperparameter is a parameter that is used to control the learning process of a neural network, opposed to other parameters that are obtained during training. 

## c)

Because the use of the softmax function normalizes the outputs in such a way that the total of the outputs equals one. Further, will the output of one object class correspond to the probability of that object being the one in the image, giving a nice interpretation of the result. 

## d)

The first task is to do a forward pass of the network. By doing the calculations, the result is that c_1 = 2, and c_2 = -4, giving that y^ = 0 and that C = 0.5
The next step is to do a backward pass. Since c_1 > c_2, max(c_1, c_2) = c_1, giving that a backward pass on the bottom half gives zero for all parameters. For the top part, we use the chain rule to compute the derivatives. The resulting derivatives is

$$
\frac{\partial C}{\partial b_1} = \frac{\partial C}{\partial \hat{y}} \frac{\partial \hat{y}}{\partial c_1} \frac{\partial c_1}{\partial b_1} = \hat{y}_n-y_n = 1
$$

$$
\frac{\partial C}{\partial b_2} = 0
$$

$$
\frac{\partial C}{\partial w_1} =  (\hat{y}_n-y_n)x_1 = -1 
$$

$$
\frac{\partial C}{\partial w_2} = (\hat{y}_n-y_n)x_2 = 0
$$

$$
\frac{\partial C}{\partial w_3} = 0 
$$

$$
\frac{\partial C}{\partial w_4} = 0 
$$

## e)

Using equation (4) in the assignment, we end up with the following weights

$$
w_{1 u} = w_1 - \alpha \frac{\partial C}{\partial w_1} = -0.9
$$

$$
w_{3 u} = w_3 - \alpha \frac{\partial C}{\partial w_3} = -1
$$

$$
b_{1 u} = b_1 - \alpha \frac{\partial C}{\partial b_1} = 0.9
$$

\clearpage

# Task 4

## a)

We see that the training is faster and the final result is better with normalized images

![](images/Task_4a.png){height=35em}


## b)

The weights for each respective digit, represented as a 28x28 grayscale image. We see that some of the pictures very clearly have the same form as the digit they represent, and for some, we have to use some imagination to see the similarities with the digit. The pictures are represented in ascending order.

![](images/task_4_b_0.jpg){height=18em}
![](images/task_4_b_1.jpg){height=18em}
![](images/task_4_b_2.jpg){height=18em}
![](images/task_4_b_3.jpg){height=18em}
![](images/task_4_b_4.jpg){height=18em}
![](images/task_4_b_5.jpg){height=18em}
![](images/task_4_b_6.jpg){height=18em}
![](images/task_4_b_7.jpg){height=18em}
![](images/task_4_b_8.jpg){height=18em}
![](images/task_4_b_9.jpg){height=18em}

## c)

Plot of the loss with learning rate lr = 1.0

![](images/task_4c.png){height=35em}

We see that the loss is much larger than with 0.0192. This comes from the gradient descent method, and how a step size (the same as learning rate) of 1.0 does not guarantee convergence of the method. Neither does a step size of 0.0192, but it is much more likely to give convergence. A method for finding lr, like line search that satisfies the Wolfe conditions would be a much better choice. 

## d)

We see that a network with a hidden layer with ReLU as the activation function performs better as the same network without the hidden layer 

![](images/task_4d.png){height=35em}