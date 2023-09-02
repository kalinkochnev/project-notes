 https://sotrh.github.io/learn-wgpu/beginner/tutorial2-surface/#state-new
`adapter` handles graphics card 
`Surface` is the part of the window that is drawn to
`adapter.features()` gives a list of features supported by graphics card
`limits` - defines the limitations of the graphics card (ex: max_texture_dimension, etc)

### SurfaceConfiguration
`usage` - defines how surface is used. `RENDER_ATTACHEMENT` says that it will be used to write to screen
`format` - defines how `SurfaceTexture` will be used on gpu (formats avail SurfaceCapabilities)
`present_mode` - how to sync the surface (window) with the display. `PresentMode::Fifo == VSync`

`CommandEncoder` creates the commands to send to the gpu. Commands are stored into a buffer before being sent into the GPU

### RenderPassDescriptor
`color_attachments` - describes where to draw the color to

### RenderPassColorAttachment
`view` describes what texture to save the colors to. Any Any colors attached will be drawn to the screen
`resolve_target` - the texture that will get the resolved output (same as view unless multisampling is enabled)
`ops: wgpu::Operations` - tells wgpu what to do with colors on screen.

### Operations
`load` - describes how to handle colors stored from previous frame
`store` - should the rendered results be stored to Texture (inside of TextureView/SurfaceTexture)


## Primitive state
`FrontFace::Ccw` indicates when vertices are arranged in CCW, then the triangle faces forward
`cull_mode: Face::Back` - when triangles are facing backwards the are culled

# Vertex Buffers
- Store data contiguously (sequential). Can represent arrays, structs, or more
- `wgpu` is notified of the structure of the buffer to be used for the shader

- `array_stride` - how many bytes a single vertex takes up (necessary to know how to skip to the next vertex, kind of like step size)

## Index buffer
A more complicated polygon is comprised of multiple triangles. To prevent duplication of data (since a polygon would have to refer to multiple vertices repeatedly), we create a sort of "look-up array"
![[Pasted image 20230724154203.png]]
^--- Notice that points B, C, and E are shared between multiple triangles

1. Create a buffer of unique vertices
2. Create an array of grouped indices that refer to the unique vertices
```rust 
const VERTICES: &[Vertex] = &[
    Vertex { position: [-0.0868241, 0.49240386, 0.0], color: [0.5, 0.0, 0.5] }, // A
    Vertex { position: [-0.49513406, 0.06958647, 0.0], color: [0.5, 0.0, 0.5] }, // B
    Vertex { position: [-0.21918549, -0.44939706, 0.0], color: [0.5, 0.0, 0.5] }, // C
    Vertex { position: [0.35966998, -0.3473291, 0.0], color: [0.5, 0.0, 0.5] }, // D
    Vertex { position: [0.44147372, 0.2347359, 0.0], color: [0.5, 0.0, 0.5] }, // E
];

const INDICES: &[u16] = &[
    0, 1, 4,
    1, 2, 4,
    2, 3, 4,
];

```
