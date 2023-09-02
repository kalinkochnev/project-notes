- Vertex shaders manipulate vertices of a triangle to transform the shape into something we want
- Vertices get converted into fragments. Each pixel of screen gets mapped to only one fragment. 
- Fragment shader determines what color the fragment is

# Clip Coordinates
https://carmencincotti.com/2022-05-02/homogeneous-coordinates-clip-space-ndc/
- It is used to determine what things are viewable by the camera

# Antialiasing
No antialiasing
![[Pasted image 20230702113300.png]]
## Multisampling
https://vulkan-tutorial.com/Multisampling
![[Pasted image 20230702113311.png]]

# Render passes
A render pass represents executing the entire rendering pipeline once. Several render passes are needed for models, lighting, post-processing, which all gets composited together 

# Shading
https://learnopengl.com/Getting-started/Hello-Triangle
Shaders are small programs that, in the end, map vertices to colored pixels on the screen.
- A **vertex shader** maps `Nothing -> Pixels`
- **Geometry shader** takes a set of vertices and can create other shapes from them (not supported in WebGPU)
- **Fragment shader** maps `Pixels -> Colors`
- The alpha/blending stage discards any elements that are hidden behind another and it blends any colors based on their opacity


**Blue squares are shaders we can control**
![[Pasted image 20230702170245.png]]


## Phong Shading
https://en.wikipedia.org/wiki/Phong_shading
An empirical model of local illumination 
Ambient light + Diffuse light + specular light = Phong Reflection
![[Pasted image 20230702120625.png]]

# Fragment Shader Interpolation
https://stackoverflow.com/questions/24441631/how-exactly-does-opengl-do-perspectively-correct-linear-interpolation