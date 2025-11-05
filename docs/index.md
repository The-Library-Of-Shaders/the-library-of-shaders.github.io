# Welcome to the Library of Shaders

The Library of Shaders is an open-source project that intends to release **copyright and license free** examples and explanations for shader effects, in order to empower developers to learn and develop shader effects.

All shader code is written to be valid **GLSL** or **OpenGL Shading Language**. We define a few variables which match the [ShaderToy](https://www.shadertoy.com/new) environment for ease of testing, but they can be swiftly adapted.


## Variables

```js
Shader Inputs
uniform vec3      iResolution;           // viewport resolution (in pixels)
uniform float     iTime;                 // shader playback time (in seconds)
uniform float     iTimeDelta;            // render time (in seconds)
uniform float     iFrameRate;            // shader frame rate
uniform int       iFrame;                // shader playback frame
uniform float     iChannelTime[4];       // channel playback time (in seconds)
uniform vec3      iChannelResolution[4]; // channel resolution (in pixels)
uniform vec4      iMouse;                // mouse pixel coords. xy: current (if MLB down), zw: click
uniform samplerXX iChannel0..3;          // input channel. XX = 2D/Cube
uniform vec4      iDate;                 // (year, month, day, time in seconds)
```

These are the uniforms defined by **ShaderToy**, and the shader examples in this library use them, as mentioned before, for ease of testing.

Other shading langages, such as Godot's shader language, are quite similar to GLSL, and therefore easy to adapt these shaders to.

## Contributing

All contributions are welcomed, and the contribution guide can be viewed on the github repository. This library is built by developers for developers, and we appreciate everyone's help.


## Licensing and Copyright

This entire library and all work inside it is licensed **CC0**. You can do anything you want with it, including clone the entire website.
