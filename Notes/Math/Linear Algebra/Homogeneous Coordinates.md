- A 3D point in cartesian coordinates can be converted to homogeneous coordinates using
$$
\begin{bmatrix}
x, y, z
\end{bmatrix} \to [x, y, z, w=1]
$$

- A point in homogeneous coordinates can be converted back to cartesian coordinates using
$$
\begin{bmatrix}
x, y, z, w
\end{bmatrix} \to \left[ \frac{x}{w'}, \frac{y}{w'}, \frac{z}{w'} \right]
$$
- Affine transformations always preserve $w=1$ (relative angles and distances are preserved)