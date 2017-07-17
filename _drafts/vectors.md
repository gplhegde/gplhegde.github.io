---
layout: post
author : Gopalakrishna Hegde
title : Vectors and vector spaces
---

# Vectors and vector spaces
We encounter numerous situations in which we have a set of numbers representing a particular entity. For example, your weight and height together representing your BMI, temperature, wind speed, humidity representing weather condition etc. When we want to do some computations on these data points to draw meaningful conclusions (for example weather forecasting), it will be easy for us to do mathematical operations if we represent them as a set of numbers called `vector` . In this article, I will briefly talk about vector and collection of vectors called `vector spaces`. Even though we will study the math concepts using simple vectors which might not have any real-life significance, once you understand the main idea, you can apply it to the kind of examples that I stated above.

## Vector 

Assuming that you know what a Cartesian coordinate system is, broadly speaking, a vector is a group of numbers that represents a point in the co-ordinate system. Each individual element in a vector is called component of the vector and total number of elements decide the dimensionality of a vector. For example, a point in a X-Y plane can be represented using a 2-dimensional vector. An important aspect about the vectors is that they have got direction. Hence we represent them using an arrow drawn form the origin to the point. You may be thinking that there can be infinite number of vectors in the same direction. You are right. That is why we associate another parameter called `magnitude` with a vector. You can consider it to be the length of the vector. Thus, all the points that lie on a line will have same direction but different magnitude.



![]({{ site.url }}/assets/vectors/simple_vector.png)



## Unit vectors

By now we know that a vector has magnitude and direction. We also know that there can be infinite number of vectors in any given direction and their magnitude differentiates them.  To make our life even simpler, what we can do is that we can have just one small vector of `length one` in a given direction. Once we have that we can use just one single number (magnitude) to represent any vector in that direction. That special vector whose length is one (unity) is called as `unit vector`. You just multiply this vector with different numbers (scalar) to get different vectors in the direction of that unit vector.

![]({{ site.url }}/assets/vectors/unit_vector.png)

Notice that we are only talking about vectors in 2-dimension. The same concept applies the vectors of any dimension. It is just that we cannot visualize them when their dimension is greater than 3.

## Linear independence  and orthogonality

Till now we have been talking about just one vector at a time. Now we will raise the bar and get into more than one.  I will now introduce two important properties of a set of vectors. Again, to keep things simple, we will consider only two vectors.

### Linear independence

When you are given with two vectors, if you can express first vector in terms of the second by scaling the second vector, then we say that the first vector linearly depends on the second vector. You can say the other way as well - the second depends on the first. In summary, this set of two vectors are said to be linearly dependent. As you already know that you can get many different vectors by multiplying a single vector with a constant, all such vectors are linearly dependent. In other words, if two vectors are linearly dependent, they lie on the same line (direction) in the X-Y plane.


$$
v_1 = \begin{bmatrix} 1 \\2\end{bmatrix} , v_2 = 2 \begin{bmatrix} 1\\2\end{bmatrix} = 2 *v_1
$$

Thus, $v_1$ and $v_2$ are linearly dependent.

If they do not lie on the same line, they we say that they are `linearly independent`.

![]({{ site.url }}/assets/vectors/linear_independence.png)

### Orthogonality

In the case of 2-dimensional vectors, if two vectors are perpendicular to each other, we will call them to be `orthogonal`. That means, one vector is 90 degrees apart from the other. They can be of any magnitude / length. We are caring only their direction here. In math words, we say that if the projection of one vector onto the other is of zero length then they are orthogonal.  To understand what a projection of vector is, we will consider a simple example in 2-dimension.

Consider two vectors $v_1$ and $v_2$ as shown below. Now lets imagine holding a torch light at the tip of $v_2$ such that the direction of light is perpendicular to $v_1$. Now you can see the shadow of $v_2$ on $v_1$. We call this to be the projection of $v_2$ on $v_1$.

Now what happens if $v_1$ and $v_2$ are perpendicular? There won't be any shadow ! That means the projection has zero magnitude. And we say that the two vectors are orthogonal.

In general, we compute the projection using an operation called dot product or scalar product which I will not talk about in this post.

![]({{ site.url }}/assets/vectors/orthogonality.png)

## Vector spaces

A vector space is a set of vectors on which certain operations and properties are defined. We will not go through all those operations and properties here. Only thing you need to know is that you can add vectors (component-wise) and multiply them with a scalar constant. You can consider X-Y plane, that you are already familiar with, to be a vector space and we will stick with 2-dimension further down the line.

As we just learned that we can add two or more vectors to get another vector, you might be thinking that we can get any vector on the X-Y plane by adding and scaling (multiplying) any two vectors. You are right, but not 100%. We need to have one more condition here. That condition is that those two vectors must be linearly independent.  Suppose, if you randomly choose any two vectors and if they happen to be on the same line, in that case you cannot get every vector on the X-Y plane by using those two vectors. In reality, you can get any vector on that line by scaling those chosen vectors and nothing other than that.  You can see this in the below figure.
With that understanding we can learn two more concepts about the vector spaces, namely span and basis of a vector space.

### Span and basis

If a set of vectors can be linearly combined to get any vector in a vector space, then we say that those set of vectors `span` that vector space. When I say linearly combined, it means that you can scale and add vectors as below.
$$
v = c_1 * v_1 + c_2 * v_2
$$
where  $v_1$ and $v_2$ are 2-D vectors.

If $v_1$ and $v_2$ are such that you can reach to any point in the X-Y plane, then we say that  $v_1$ and $v_2$ span the 2-D space. Now look at below figure containing two vectors and a point ( tip of another vector) that we want to reach by combining these two vectors. Can we achieve our target? Definitely not. Why because, these two vector are linearly dependent as you can see. $v_2 = 1.5 * v_1$ in this case (right side plot in the below fig).

Now consider the case where two vectors are not along the same line. Here two vectors are linearly independent and hence we can get any vector in the 2-D vector space by linearly combining them. We show few target vectors that we get by combining these two vectors (left side plot in the below fig).


![]({{ site.url }}/assets/vectors/span_basis.png)

If a set of vectors are linearly independent and span the n-dimensional vector space, then this set of vectors are called as `basis vectors` of that n-dimensional vector space. You can consider them as basic building blocks using which you can construct any other vector in that space. If every vector in this set ( basis) is orthogonal to every other vector, then we call them as `orthogonal basis`.  On top of that, if all of them  happen to be  unit vectors, then we term them as `orthonormal basis` vectors.

Now, can you think of the orthonormal basis for 2-D space - XY plane? In fact, X and Y axis themselves are the orthonormal basis.
$$
b_0 = \begin{bmatrix}1\\0\end{bmatrix} = X-axis,  \hspace{1cm} b_1 = \begin{bmatrix}0\\1\end{bmatrix} = Y-axis
$$
Now you may be thinking that a vector space can have many such basis vectors. You are right. In fact, a space has infinite number of basis vectors. But why X and Y axis are widely used? One simple reason is, when the basis is orthonormal, each component of any vector is just orthogonal projection of that vector onto corresponding basis vector. That is, first component of a 2-D vector is orthogonal projection of that vector onto X-axis and the second component is simply the orthogonal projection onto Y-axis.

Thats all we need to know as of now to proceed to next article about matrices! Hope you enjoyed learning about vectors and vector spaces.





