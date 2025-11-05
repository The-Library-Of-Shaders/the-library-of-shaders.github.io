# The-Library-Of-Shaders 
https://snorfield.github.io/The-Library-Of-Shaders/

Library of GLSL shaders and explanations to empower developers to learn shader development.


## Contribution Rules

So you want to add your own articles or other stuff to this project. That's awesome, there's just a few rules for contribution.

### Rule 1
Use the ShaderToy uniforms in all your code.

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

It's recommended to also test the code before committing it. :)

### Rule 2

Always include detailed explanations on what the shader is doing and the math behind it. The Library of Shaders is here to help developers understand effects, not just copy and paste them.


### Rule 3

You agree that your code and articles are licensed **Creative Commons Zero**, and require no credit for developers to use them.



