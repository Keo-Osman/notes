---
tags:
  - CS/rendering
---
When we want to render an object we must first break it down into triangles, then when we want to render a triangle the 3 vertices’ coordinates *6 numbers in total* are given as input and an image that best represents this theoretical perfect triangle. So we need to decide which pixels are mostly contained within the triangle then colour them.

**The graphics pipeline is a linear sequence of stages where each stage takes in some input as data then performs some operation and outputs it onto the next stage**

# High level overview 
## Stage 1: Input Assembler
This stage takes a list of numbers and groups them together into geometry, for example every 6 numbers could be used to make a new triangle
## Stage 2: Vertex Shader
The vertex shader process each vertex individually and performs transformations such as translation and rotation
## Stage 3:  Rasterization
Rasterization takes some geometry and determines which pixels are part of it and groups them into a fragment
## Stage 4: Fragment Shader
The fragment shader processes each fragment individually and outputs values such as colour from given input of lighting normals and textures etc..
## Final Stage Colour Blending
The colour blending stage applies operations to mix the values of multiple fragments that correspond to the same pixel

# Fixed Function vs Programmable
There are 2 types of stages in the graphics pipeline, fixed function and programmable. 
Fixed function stages include:
- Input assembler
- Rasterization
- Colour blending
This means as programmers we have less control over operations and can only really configure them by changing variables whereas programmable stages such as:
- Vertex shader
- Fragment shader
Can be changed by uploading our own code to the GPU, *These stages are written in a C-like language called* **GLSL**