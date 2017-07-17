---
layout: post
title : Matrices and linear transformations
---

# Matrices and linear transformations
Matrices are convenient mathematical constructs that makes our life easy.  This article gives a brief understanding of what matrices actually are and their geometrical interpretation. This is not a self-contained article. You may want to refer to the [previous]() article on vectors and vector spaces to better correlate the concepts. In this article, I will not give any formal definitions and also may not stick with standard mathematical notations just to keep things simple. As we proceed, I will also try to give real world examples that will help you to correlate better.

In the previous post on vectors, we talked about representing entities that contain more than one parameters such as BMI as vectors. What if you have such data collected from many people? How do you bring that data into the mathematical  construct? You can have as many vectors as the number of people. However, we have much easier way to contain them in the form of a matrix. You create vector from each data point and stack them side-by-side and you will end up creating a nice matrix for the entire dataset you have. We consider 3 such data points and create a matrix $M$ as shown below.
$$
v = \begin{bmatrix}height\\weight\end{bmatrix}\hspace{2cm} v_1 = \begin{bmatrix}1.5\\52\end{bmatrix}, v2 = \begin{bmatrix}1.65\\65\end{bmatrix}, v_3 = \begin{bmatrix}1.8\\80\end{bmatrix}\\
M = \begin{bmatrix}v_1 \hspace{1cm}v_2\hspace{1cm}v_3\end{bmatrix} = \begin{bmatrix}1.5&1.65&1.8\\52&65&80\end{bmatrix}
$$

Here matrix $M$ has 2 `rows` and 3 `columns` or it is of dimension $2 \times 3$. Lets represent this with $M_{2\times3}$ or $M_{m\times n}$ in general.  In this example, each column of the matrix $M$ is a 2-D vector - height and weight being the two dimensions. You can stack more columns to add height and weight of more friends. Each column will represent a point in 2-D plane. Lets call it height-weight 
plane OR $H - W$  plane.

![Height - Weight plane representing above 3 vectors]()

This is nothing but $X-Y$ plane that we learned in the previous article. I just gave different names for axes to give them real-world significance. You can consider this plane to be a 2-D vector space whose basis vectors are,

​										 $$h = \begin{bmatrix}1\\0\end{bmatrix} \hspace{2cm} w = \begin{bmatrix}0\\1\end{bmatrix}$$

In this formulation,  the number of rows ($m$) represent the `dimension` of the space and number of columns represents number of vectors of that dimension (is of less significance as you can add more such vectors without affecting the property of the space).

We know that each vector (data point) in the vector space (interchangeably referred as space) can be represented as linear combination of its basis vectors. For example,
$$
v = c_1*h + c_2 * w
$$
Now, can you guess what are the values of $c_1$ and $c_2$ for the vector $v_1$? Since the basis is orthonormal, the scaling factors $c_1$ and $c_2$ are in fact  vector $v_1$'s components themselves.
$$
v = c_1 * \begin{bmatrix}1\\0\end{bmatrix} + c_2 * \begin{bmatrix}0\\1\end{bmatrix}\\
v_1 = 1.5 * \begin{bmatrix}1\\0\end{bmatrix}  + 52 * \begin{bmatrix}0\\1\end{bmatrix}
$$
where $v_h$ and $v_w$ are $h$ and $w$ components of the vector $v$ in our $H-W$  plane.

How about stacking those two basis vectors into another matrix, say matrix $B$ like below.
$$
B = \begin{bmatrix}1&0\\0&1\end{bmatrix}
$$
This special matrix's name is `identity matrix` and we will learn more about this when we talk about transformations later in this article.

There are several operations like addition, multiplication defined on matrices. You might be already knowing about these operations. The operation of our interest in this article is matrix multiplication. Lets talk about that now.



# Matrix multiplication - linear transformation

You may be already knowing about the way to multiply two matrices. You perform element-wise multiplication and addition between row of the first matrix and column of the second. To do that,  the number of columns in the first matrix and number of rows in the second matrix must be same. Have you ever given a thought as to why matrix multiplication is defined like that? Let's see why is that.

Matrix - matrix multiplication or matrix - vector (vector is also a matrix with one column) multiplication is a linear transformation. What does that even mean? Lets get back to our  $H- W$ plane example where we have collected height and weights of different people and nicely arranged in a matrix $M$. Now lets say that a person's heart rate (R) and blood pressure (P) level is directly dependent on his height and weight (yes, I am making this up!). We can transform height and weight vector into another vector whose elements are R and P. We can do that by multiplying a H-W vector by a matrix called transformation matrix $T$. We can create (learn) such a matrix given lot of height and weight data points using machine learning but we will get into in this post.

![image on transformation from one space to other]()

Lets say one such matrix is $T = \begin{bmatrix}1&2\\3&2\end{bmatrix}$. The columns of the transformation matrix are actually the transformed $h$ and $w$ axis. Meaning, the basis vector $h = \begin{bmatrix}1\\0\end{bmatrix}$ got transformed into r = $\begin{bmatrix}1\\3\end{bmatrix}$ and $w = \begin{bmatrix}0\\1\end{bmatrix}$ got transformed into $p = \begin{bmatrix}2\\2\end{bmatrix}$.  Lets call the transformed space as R-P space with $r$ and $p$ as its basis vectors. Now, how do you represent any vector in this space? Linear combination of these two vectors right? Lets represent vectors in this new space using $u$ instead of the $v$ that we used for H-W space. Now any vector $u$ in R-P space can be written as,
$$
u = c_1 * r + c_2 * p = c_1 * \begin{bmatrix}1\\3\end{bmatrix} + c_2 * \begin{bmatrix}2\\2\end{bmatrix}
$$
Also, we had any vector $v$ in H-W space as
$$
v = c_1 * \begin{bmatrix}1\\0\end{bmatrix} + c_2 * \begin{bmatrix}0\\1\end{bmatrix}\\
$$
You can see that the only change that occurred when we transformed our vectors from H-W space into R-P space (derive heart rate and blood pressure from height and weight) is to the basis vectors! The scaling factors $c_1$ and $c_2$ still remain the same but the vectors that they scale (basis vectors) changed. In H-W space the basis vectors were orthonormal and hence the scaling factors were vector components themselves. However, in the new R-P space, the basis vector $r$ and $p$ are no more orthonormal and you need to perform multiplication with non-trivial numbers to get the transformed components. In summary, what I just explained is matrix-vector multiplication as a process of transforming a vector from one space to the other whose basis vectors are packed into a transformation matrix  $T$. Here is how we write it.
$$
u = Tv = T \begin{bmatrix}c_1\\c_2\end{bmatrix} = \begin{bmatrix}1&2\\3&2\end{bmatrix}  \begin{bmatrix}c_1\\c_2\end{bmatrix} =  \begin{bmatrix}c_1+2c_2\\3c_1 + 2c_2\end{bmatrix}
$$
Which is noting but multiplying rows of the first matrix with the columns of the second! Thus our height-weight vector $v_1$ get transformed into say $u_1$ as below.
$$
u_1 = Tv_1 = \begin{bmatrix}1&2\\3&2\end{bmatrix}  \begin{bmatrix}1.5\\52\end{bmatrix} = \begin{bmatrix}105.5\\108.5\end{bmatrix}
$$


Now matrix-matrix multiplication is just transforming many vectors which are stacked side-by-side into a matrix. For example, $M$ gets transformed into $M^{'}$
$$
M^{'} = TM =  \begin{bmatrix}1&2\\3&2\end{bmatrix} \begin{bmatrix}1.5&1.65&1.8\\52&65&80\end{bmatrix} = \begin{bmatrix}105.5&131.65&161.8\\108.5&134.95&165.4\end{bmatrix}
$$

# Rank, inverse and determinant of a matrix

The example of transforming height and weight to deduce heart rate and blood pressure makes little sense, nonetheless it helped us to understand matrix multiplication as applied to real-world data. Now the question is, can we get back the original height and weight vector $v$ from the vector $u$? That is, can we inverse this transformation? We can do so, but not always. We can reverse the transformation by multiplying the transformed vector by the inverse of transformation matrix if the inverse exists. We denote this as $v = T^{-1}u$.  What are the conditions for the existence of inverse? Before diving into that, we need to understand rank of a matrix.

The rank of a matrix $T$ is simply the number of independent columns (vectors) of that matrix. In the 2-D case, how many column vectors of the matrix point in the different direction (or do not lie along same line). In out example, the transformation matrix $T$ has two columns which are independent. What happens if one column of $T$ is dependent on the other? In this case, the space spanned by the columns of $T$ becomes 1-dimensional. Thus the rank of $T$ becomes 1 and every transformed vector $u$ lies along same line ! In other words, every vector $v$ in our 2-D space gets mapped on a single line as show below. Thus there is no way that we can get back those original vectors $v$ from $u$. 

![image showing non-invertible transformation]()

Matrix inverse is defined for square matrices ($m = n$). That is, the dimension of the original and transformed space are same. We need $m$ independent vectors as the basis of the transformed space and hence the inverse is possible if the rank is equal to $m$. We will not discuss about how to compute the inverse of a matrix in this article. 

## Determinant

The absolute value of the determinant determinant of a matrix $T$ is the area spanned by its column vectors in case of vectors in 2-D space as shown below. For 3-D space it is the volume and for m-dimensional space it is hyper-volume.

![area spanned by 2 vectors in 2-D]()

The determinant of a matrix
$$
T = \begin{bmatrix}a&b\\c&d\end{bmatrix} 
$$
is thus the area spanned by vectors $\begin{bmatrix}a\\c\end{bmatrix}$ and $\begin{bmatrix}b\\d\end{bmatrix}$ and is equal to $a*d - b*c$ as shown below. The determinant is a scalar quantity.

![area spanned by two general vectors]()

You can now figure out the way to compute the volume spanned by three 3-D vectors and you will end up with a formula for computing determinant of a $3\times3$ matrix.

If a the columns of 2$\times$2 transformation matrix are along same line, then the area spanned by them is zero. If any two columns of a $3 \times 3$ matrix are dependent then the volume spanned by them is zero or is all there of them are dependent then both the volume and area spanned by them is zero. In such cases the determinant will be zero and there is no inverse for such matrices. Thus, inverse of a transformation is only possible when the determinant of the transformation matrix is non-zero.

Another important use of the determinant is in normalizing the multivariate Gaussian probability density function. Thats why use  see the determinant of the covariance matrix $\Sigma$ in the denominator of the density function.
$$
p_x(x_0...x_n) = \frac{1}{\sqrt{2\pi |\Sigma|}} . exp\left(-\frac{1}{2} (x -\mu )^{T}\Sigma^{-1}(x-\mu)\right)
$$
```

```
