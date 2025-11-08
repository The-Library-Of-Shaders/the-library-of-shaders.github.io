# Welcome to the Library of Shaders

The Library of Shaders is an open-source project that intends to release **copyright and license free** examples and explanations of miscellaneous shader effects, in order to empower developers to learn and develop shader effects themselves.

All shader code here is written in valid **GLSL** or **OpenGL Shading Language**.


## Variables

We define a few variables that match the [ShaderToy](https://www.shadertoy.com/new) environment for ease of testing, but they can be easily adapted if you use another shader language (e.g. Godot's shader language) as needed.

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

If ShaderToy does not have a uniform for a certain thing that the shader requires, it will be explained in the article, and the uniforms will still follow the naming convention for ShaderToy. An example of this is **vertex shaders**. Because ShaderToy is mainly a playground for **fragment shaders**, there's nothing like `uniform mat4 iModel;`. However, we still have a section for vertex shaders, they just won't be able to run in the ShaderToy environment.

Articles will explain any uniforms not available in ShaderToy.

## Contributing

All contributions are welcomed, and the contribution guide can be viewed on the [GitHub repository](https://github.com/Snorfield/The-Library-Of-Shaders). This library is built by developers for developers, and we appreciate everyone's help.

We strive to follow the principals of the [5 Wikipedian Pillars](https://en.wikipedia.org/wiki/Wikipedia:Five_pillars).

## Licensing and Copyright

This entire library, and all work inside of it, is licensed under **Creative Commons Zero**. You can read the full text [here](https://github.com/Snorfield/The-Library-Of-Shaders/blob/main/LICENSE).
