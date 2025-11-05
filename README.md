# The Library Of Shaders 
https://snorfield.github.io/The-Library-Of-Shaders/

Copyright and license free library of shaders and explanations to empower developers to learn shader development


## Contribution Rules

So you want to add your own articles or other stuff to this project. That's awesome, there's just a few rules for contribution.

If the ShaderToy uniforms (below) has a variable for something you need in your shader, use it. If not, follow the ShaderToy naming style and explain what the variable is in your article. An example of this would be if you need the camera position for your shader to function. Define it as `iCameraPosition`, and also specify the type. So, `uniform vec3 iCameraPosition`.

```js
// ShaderToy uniforms
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

For certain effects that may use more then four input channels, you should specify that it won't work in ShaderToy in the article, and then continue incrementing the `iChannel` value by one (e.g `iChannel4`).

It's recommended to also test the code before committing it. :)

Always include detailed explanations on what the shader is doing and the math behind it. The Library of Shaders is here to help developers understand effects, not just copy and paste them.

You agree that your code and articles are licensed **Creative Commons Zero**, and require no credit for developers to use them.

Write the code to be proper **GLSL** or **OpenGL Shading Language**, in terms of syntax. 



