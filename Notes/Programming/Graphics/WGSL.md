`@builtin(position)` - indicates to use for clip coordinates
- x and y are (width pixels) and (height in pixels)
- y=0 is top of screen
- Have to store actual position and pixel coordinates separately

# Entrypoints
- WGSL only includes functions/variables that are used by its entrypoints

`@vertex` - mark as entrypoint for vertex shader
`@fragment` - mark as entrypoint for fragment shader
`@compute`

# Attributes
`@location(number)` defines the inputs and the outputs of the shader. The inputs are supplied by vertex buffers.

- `@location()` can be used as inputs for a shader
## example
```rust
struct Vertex {
	@location(0) position: vec2f,
	@location(1) color: vec3f,
};
@vertex vs2(s: Vertex)
```
**configuration:**
```json
buffers: [
  {
    arrayStride: (2 + 3) * 4, // (2 + 3) floats, 4 bytes each
    attributes: [
      {shaderLocation: 0, offset: 0, format: 'float32x2'}, // position
      {shaderLocation: 1, offset: 8, format: 'float32x3'}, // color
    ],
  },
],
```
**diagram:**
![](https://webgpufundamentals.org/webgpu/lessons/resources/vertex-buffer-mixed.svg)
## inter-stage variables
Can also pass locations around between vertex and fragment shaders
```rust
struct VSOut {
  @builtin(position) pos: vec4f,
  @location(0) color: vec4f,
  @location(1) texcoords: vec2f,
};
struct FSIn {
  // same locations
  @location(1) uv: vec2f, // received from VSOut.texcoords
  @location(0) diffuse: vec4f, // received from VSOut.color 
};

@vertex fn foo(...) -> VSOut { ... }
@fragment fn bar(moo: FSIn) ...
```

## fragment shader output
Locations are used to indicate where to store the results in for `GPURenderPassDescriptor.color_attachment`

## Built ins
`@builtin(name)` - specify a variables value comes from feature of WebGPU

![[WebGPU#Vertex Buffers]]


`@location(0)` means store into first color target



- Can cast types with `f32()` or `i32()`
- `var` can be modified but must have specified typed
- `let` can have type inferred but value cannot be changed
- Vector types are generic
