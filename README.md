# Optic Flow 
This is a simple implementation of Optic Flow in Python. 

The program takes a short video clip as input and shows optic flow for a collection of consecutive frames.

Possible optic flow parameters to track are:
* Translation in x and y direction
* Rotation around z axis
* Scale

## Theory
Optic flow takes in two collections of pixels in two consecutive frames and calculates partial derivatives of the pixel coordinates with respect to time. The partial derivatives are then used to calculate the optic flow parameters.

### Example
Consider the following two frames:
$$
\begin{align}
I_1 &= \begin{bmatrix}
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix} \\
I_2 &= \begin{bmatrix}
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
\end{align}
$$

You will notice that the pixel in the middle of the first frame has moved one pixel up and one pixel right in the second frame. This is the translation in x and y directions. 
The rotation around the z axis is zero, because the pixel has not rotated. The scale is one, because the pixel has not changed size.

we can calculate the partial derivatives of the pixel coordinates with respect to time as follows:
$$
\begin{align}
\frac{\partial x}{\partial t} &= \frac{1}{2} \cdot \frac{\partial I_2}{\partial x} - \frac{1}{2} \cdot \frac{\partial I_1}{\partial x} \\
\frac{\partial y}{\partial t} &= \frac{1}{2} \cdot \frac{\partial I_2}{\partial y} - \frac{1}{2} \cdot \frac{\partial I_1}{\partial y}
\end{align}
$$

