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
N_{w i} = F_{conv i}^2 * C_{i-1} * C{i}
$$

For the different layers we get

$$
N_{w 1} = 800
$$
$$
N_{w 2} = 18432
$$
$$
N_{w 3} = 73728
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


# Task 2

## a)

Plot of the training and validation loss

![](images\task2a_plot.png){height=25em}

A sign of overfitting is that the CNN has higher accuracy for the training set than the test set, indicating that the network is starting to "specialize" in recognizing the training set, not the general attribute/object the training set is set to represent. If the training loss is lower than the test loss, this is an indication on overfitting. As we see from the figure, this is not happening in our network.  

## b)

Plot of the training and validation loss running with Adam and SDG algorithms as optimizers

![](images\task2b_plot.png){height=25em}

## c)

Visualized filters and activations

![](images\task_2c.png){height=35em}

## d)

The first filter, represented by the two images to the left, looks like is extracting the vertical edges of the image. The activation shows mostly vertical edges and the visualization of the filter looks like a vertical sobel filter. The second image looks like it is extracting fine edges parallel to the diagonal from the top left corner to the bottom right. Again the activation contains only fine diagonal edges and the filter looks like a diagonal sobel filter. The mid filter seems to extract the foreground of the image, filtering out both the horizon and the zebra. However, it still gives some activation to the zebra, effectively dividing the image in three objects. The filter visualization have a lot of green, possibly representing the greenish foreground. The next filter seems to extract the edges of the zebra. The activation mostly contains edges consistent with the edges of the zebra. The last filter seems to extract the sky. Again the activation views three different objects and the visualized filter have a lot of blue, the same as the sky.


# Task 3

## a)

First of all will vertical stripes give horizontal frequency components and visa versa. Further will large frequencies in the spatial domain (like 1a) give frequency components far from the origo than smaller frequencies.
Since 1a have the larges frequency with horizontal stripes, it maps to 2e which have the largest vertical frequency components. The rest of the mappings follow the same reasoning. 

| Spatial domain | Frequency domain |
|:--------------:|:-----------:|
|       1a       |      2e     |
|       1b       |      2c     |
|       1c       |      2f     |
|       1d       |      2b     |
|       1e       |      2d     |
|       1f       |      2a     |

## b)

High-pass filters are filters that filters out low frequencies and let high frequencies thought. Low-pass filters do the opposite. 

## c)

We know that that small frequency components are centered around the origo (center of the kernel). Convoluting a) with a picture (multiplying in the frequency domain) will remove the low frequency components as black corresponds to 0 in the kernel. Hence is a) a high-pass filter.
The opposite is true for the b) kernel, hence it is a low-pass filter.


# Task 4

## a)

Images of the different steps doing low-pass filtering of the "camera man" image.

![](images/task4a_low-pass.png){height=25em}

Images of the different steps doing high-pass filtering of the "camera man" image.

![](images/task4a_high-pass.png){height=25em}

The ringing effect appears since we are using box filters to filter the image. A box filter is a filter with sharp edges. A box inverse Fourier transformed gives a sinc response, resembling a ringing effect. This can be avoided by using a gaussian approximation instead of a box filter. 


## b)

A image filtered by the gaussian filter

![](images/camera_gaussian.png){height=25em}

A image filtered by the horizontal sobel filter

![](images/camera_sobelx.png){height=25em}

## c)

Image showing the filtered moon. 

![](images/moon_filtered.png){height=25em}

The image was filtered by masking out all the vertical frequency components (horizontal in the frequency domain) except those close to the origo.


## d)

Image of the different steps resulting in a rotated image of the scanned pages.

![](images/task4d.png){height=25em}