# World transformation
- Transforms a model's vertices from object space (the space the model was created) into world space

# View Transform
- World space needs to be transformed into a space that is relative to the view of the camera
- Usually

## Look at camera 
https://www.mauriciopoppe.com/notes/computer-graphics/viewing/view-transform/
![[Pasted image 20240310231424.png]]
# Projection Transform
- Vertices transformed into the view space need to be projected onto a 2D space to be displayed to the user

$$
A =  P_{view}^{canvas} V_{world}^{view} W_{\text{model}}^{world
} \text{model}
$$

# Coordinate systems
- There is a difference between right handed and left handed coordinate systems
https://www.3dgep.com/3d-math-primer-for-game-programmers/