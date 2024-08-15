**Source:** https://www.scratchapixel.com/lessons/3d-basic-rendering/3d-viewing-pinhole-camera/virtual-pinhole-camera-model.html
# Physical pinhole model
**Image plane** - the back face of the camera where the image is projected onto
![[Pasted image 20240303105008.png]]
- It forms an inverted image onto the other side
![[Pasted image 20240303105342.png]]
- Larger aperture makes the image blurry because there is overlap
- Needs longer exposure in order to get enough light to hit
- Lenses are used to get as much light as possible but focus the rays back down to a single point
![[Pasted image 20240303105703.png]]

**Depth of field** - the distance between the nearest and farthest object from the scene the appears reasonably sharp (sharpness depends on distance)
- Pinhole cameras have infinite depth of field while normal cameras do not

![[Pasted image 20240303105601.png]]

**Focal length** - the distance from the hole the light enters the camera to the image plane (where the image is projected onto)
- As focal length increases, the size of the image increases
- You can zoom in by increasing focal length, zoom out be decreasing focal length
![[Pasted image 20240303105826.png]]
- Changing the focal length is equivalent to changing the angle of view (decreased focal length increases angle of view)
![[Pasted image 20240303110117.png]]

- There are two angles of view, horizontal and vertical
- They are related by the aspect ratio so you only need to define one of the field of field of views
![[Pasted image 20240303110330.png]]



- AB = focal length slash distance to canvas
- BC = 1/2 canvas size
- $\theta$ = half FOV
$$
\begin{align}
\tan \theta&=\frac{BC}{AB} \\
BC &= AB \tan(\theta) \\
2* BC &= 2 * AB \tan \theta = \text{Canvas size}
\end{align}
$$
![[Pasted image 20240303110546.png]]

- Larger image surfaces have larger FOVS (red=small, blue=big)
- If have a small film, you need a small focal length
- angle of view depends on focal length and film size

![[Pasted image 20240303110857.png]]

$$
\text{Aspect Ratio} = \frac{width}{height}
$$
- Not preserving canvas aspect ratio and raster image aspect ratio leads to stretching in x or y
![[Pasted image 20240303111330.png]]

# Virtual Pinhole Model

- The image plane in CG is position in front of camera aperture than behind it b/c the image would be upside down
![[Pasted image 20240303111608.png]]

- Objects closer than near-clipping plane or farther than far-clipping plane are invisible
- The $-z$ axis is defined as the direction the cameras is looking in
- Assume the canvas is at the near clipping plane
![[Pasted image 20240303111900.png]]
![[Pasted image 20240303112528.png]]
$$
\begin{align}
\text{Canvas size} = 2 * \tan(\frac{\theta}{2}) * \text{distance to canvas} \\
\text{Canvas size} = 2 * \tan(\frac{\theta}{2}) * Z_{near}
\end{align}
$$
- $Z_{near}$ is the distance from the eye to the clipping plane along the camera's local z-axis
![[Pasted image 20240303112414.png]]

- A point is only visible if, after projection, it is within the canvas boundaries
- If we know the corner points of the canvas we can easily check if a point is in bounds
![[Pasted image 20240303112212.png]]
```c++
float canvasSize = 2 * tan(angleOfView * 0.5) * Znear;
float top = canvasSize / 2;
float bottom = -top;
float right = canvasSize / 2;
float left = -right;
// compute projected point coordinates
Vec3f Pproj = ...;
if (Pproj.x < left || Pproj.x > right || Pproj.y < bottom || Pproj.y > top) {
    // point outside canvas boundaries. It is not visible.
}
else {
    // point inside canvas boundaries. Point is visible
}
```

- By default cameras are located at origin and points along negative z-axis
- camera-to-world transform $H_{camera}^{world}$ orients the camera
- In rasterization the inverse matrix converts points from global to camera space $H_{world}^{camera}$ 
![[Pasted image 20240303112852.png]]

# Perspective transformation
**The projection matrix attempts to remap values projected onto the image plane onto a unit cube** (basically normalized)
![[Pasted image 20240303121747.png]]


![[Pasted image 20240303113447.png]]
 
- $P$ is the point we want to project, $P_{s}$ is the projected point onto the image plane

By similar triangle
$$
\frac{AB}{DE} = \frac{BC}{EF}
$$
Let $AB=Z_{near}$ and $DE=P_{Z}$ (z coordinate of P), $EF=P_{y}$, and $P_{sy}$ is the projected y-coordinate

$$
\begin{align}
\frac{Z_{near}}{P_{Z}} = \frac{P_{sy}}{P_{y}} \\
P_{sy} = P_{y} \frac{Z_{near}}{P_{z}}
\end{align}
$$
The negative $z$ direction is movement forward from the lens of the camera (based on how we defined the coordinate frame)
The projected point along the x-axis is
$$
\begin{align}
\frac{Z_{near}}{P_{Z}} = \frac{P_{sx}}{P_{x}} \\
P_{sx} = P_{x} \frac{Z_{near}}{-P_{z}}
\end{align}
$$

## Mapping onto the unit cube
**For the x coordinate**
Assume $P_{sx}$ is visible and $l, r$ and the left and right bounds respectively
$$
\begin{align}
l \leq P_{sx} \leq r \\
0 \leq P_{sx}-l \leq r- l \\
0 \leq  \frac{P_{sx}-l}{r-1} \leq 1  \\
0 \leq  2\frac{P_{sx}-l}{r-1} \leq 2  \\
-1 \leq  2\frac{P_{sx}-l}{r-1} - 1 \leq 1   \\
\text{clever form of one}\\
-1 \leq  2\frac{P_{sx}-l}{r-1} - \frac{r-l}{r-l} \leq 1 \\
-1 \leq  \frac{2P_{sx}-2l - r +l}{r-1}\leq 1  \\ \\
-1 \leq  \frac{2P_{sx}-r-l}{r-1}\leq 1  \\
-1 \leq  \frac{2P_{sx}}{r-1} - \frac{r+l}{r-1}\leq 1
\end{align}
$$
Substitute the definition of $P_{sx}=P_{x} \frac{Z_{near}}{-P_{z}}$ 

$$
\begin{align}
-1 \leq  \frac{2P_{sx}}{r-1} - \frac{r+l}{r-1}\leq 1 \\
-1 \leq  \frac{2P_{x}Z_{near}}{-P_{z}(r-1)} - \frac{r+l}{r-1}\leq 1 \\
\end{align}
$$

We can shove these terms into a matrix if we assume that we divide by $-P_{Z}$ at the end. ==this matrix is in column major order (rows are the column vectors)==
$$
\begin{align}
\frac{-1}{P_{z}} \left[\begin{array}{cccc}
\dfrac{2n}{r-l} & 0 & \dfrac{r + l}{r-l} & 0 \\
\ldots & \ldots & \ldots & \ldots \\
\ldots & \ldots & \ldots & \ldots \\
0 & 0 & -1 & 0\\
\end{array}\right] * \left[ \begin{array}{c}x \\ y \\ z \\ w\end{array}\right] \\ \\
P_{sy} = \left( \frac{1}{-P_{z}} \right) \left( \left( \frac{2n}{r-l} \right) P_{x} + 0 P_{y}  + \frac{r+l}{r-l} P_{z}\right) \\
=\frac{2P_{x}Z_{near}}{-P_{z}(r-1)} - \frac{r+l}{r-1}
\end{align}

$$

**For the y coordinate**
Replace $l$ w/ $b$ (bottom) and $r$ w/ t (top)
$$
-1 \leq \frac{2n P_y}{-P_z(t-b)} - \frac{t + b}{t - b} \leq 1.
$$

**Current progress**
$$
\left[\begin{array}{cccc}
\frac{2n}{r-l} & 0 & \frac{r + l}{r-l} & 0 \\
0 & \frac{2n}{t-b} & \frac{t + b}{t-b} & 0 \\
\ldots & \ldots & \ldots & \ldots \\
0 & 0 & -1 & 0\\
\end{array}\right]
$$


**For the z coordinate** the projected x and y do not affect the z coordinate.
Remember that to convert between homogeneous and cartesian coordinates we have to divide by $w$. [[Homogeneous Coordinates]]
- $P_{w}$ is equal to 1

$$
\left[\begin{array}{cccc}
\frac{2n}{r-l} & 0 & \frac{r + l}{r-l} & 0 \\
0 & \frac{2n}{t-b} & \frac{t + b}{t-b} & 0 \\
\color{green}{0} & \color{green}{0} & \color{red}{A} & \color{red}{B}\\
0 & 0 & -1 & 0 \\
\end{array}\right]
$$
$$

Ps_z = \frac{0 \cdot P_x + 0 \cdot P_y + A \cdot P_z + B \cdot P_w}{Ps_w = -P_z} \rightarrow \frac{A \cdot P_z + B}{Ps_w = -P_z}.
$$

- We know that $P_{z}$ when it is on the far clipping plane must be mapped to one
- We also know that $P_{z}=0$ when it is on the near clipping plane
- $n, f$ are the near and far clipping distance
- Since z-coordinates of all points projected onto the image plane are negative, scale $n, f$ to $-n, -f$

Need to solve
$$
\left\{ \begin{array}{ll} \frac{(P_z=-n)A + B}{(-P_z=-(-n)=n)} = -1 & \text{ when } P_z = n\\ \frac{(P_z=-f)A + B}{(P_z=-(-f)=f)} = 1 & \text{ when } P_z = f \end{array} \right. \\ \rightarrow  \left\{ \begin{array}{ll} {-nA + B} = -n & (1)\\  {-fA + B} = f & (2) \end{array} \right.
$$

Our final matrix (in column major order) is 
$$
\left[\begin{array}{cccc} \frac{2n}{r-l} & 0 & \frac{r + l}{r-l} & 0 \\ 0 & \frac{2n}{t-b} & \frac{t + b}{t-b} & 0 \\ 0 & 0 & -\frac{f+n}{f-n} & -\frac{2fn}{f-n}\\ 0 & 0 & -1 & 0\\ \end{array}\right]
$$

## Finding top, bottom, left, right coordinates
- We use the aspect ratio and the FOV to figure them out
![[Pasted image 20240303123356.png]]

$$
\begin{array}{l} 
aspect\;ratio = \frac{width}{height}\\ 
top = \tan( \frac{ FOV } {2}) * near \\ 
bottom = -top \\ right = top * aspect\;ratio\\ 
left = bottom = -top * aspect\;ratio 
\end{array}
$$