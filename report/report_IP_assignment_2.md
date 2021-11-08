---
# These are meta-variables defined with YAML syntax, change them as you wish.
# see https://pandoc.org/MANUAL.html#variables
title: TDT4195 IP Assignment 1
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

Sampling is how we divide a continuous space into a discretized space, digitalizing it and making it possible to quantize the space.

## b)

Quantization is the digitalization of the amplitude (f. ex. light intensity) for each of the sampled parts of the space. 

## c)

If the distribution of pixels is equally distributed over the range of the intensity values in an image histogram, we can see that the picture will have high contrast. 
In other words, if the histogram is flat will the picture have high contrast.

## d)

The first step is to compute H_r(r) by counting the different pixel intensities. Further, the PDF and CDF was computed using 

$$ 
p_r(r_k) = \frac{H_r(r)}{MN} 
$$
$$
F_r(r_k) = \sum_{j=1}^{k} p_r(r_j)
$$  

Last, the transformation was computed using

$$
T(r) = \left \lfloor{(L-1)F_r(r)}\right \rfloor 
$$

The results from the computations is shown in the table below


| r | H_r(r) | p_r(r_k) | F_r(r_k) | T(r) |
|---|--------|----------|----------|------|
| 0 |    1   |  0.0667  |  0.0667  |   0  |
| 1 |    1   |  0.0667  |  0.1333  |   0  |
| 2 |    0   |     0    |  0.1333  |   0  |
| 3 |    1   |  0.0667  |  0.2000  |   1  |
| 4 |    2   |  0.1333  |  0.3333  |   2  |
| 5 |    2   |  0.1333  |  0.4667  |   3  |
| 6 |    4   |  0.2667  |  0.7333  |   5  |
| 7 |    4   |  0.2667  |     1    |   7  |


Using the transformation s = T(r) on the provided image yields the following image

![](images/Task_1_d.PNG){height=10em}


## e)

If we apply a log transform to an image with large variance in the pixel intensities will the low intensities be widened and the bright intensities squeezed. This will be the same as reducing the dynamic range of an image, making it easier for the human eye to observe the details of both the part of the picture with low intensities and bright intensities. 

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