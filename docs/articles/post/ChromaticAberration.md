# Chromatic Aberration

Chromatic Aberration is an effect commonly observed in images, when the camera can't focus all color channels onto a point. This results in different colors being in slightly different positions.

In shaders, this effect can be simulated by offsetting the position at which we sample each color channel. This is quite simple, but the value by which you offset needs to be quite small to look any good.

Let's first assume a couple variables we have access to.

* `fragCoord`
* `iResolution`

These are explained on the home page, under variables.

Let's grab the normalized coordinates of our pixel. Since `fragCoord` ranges from 0 to the screen dimensions, we just need to divide by the screen dimensions.

```js
vec2 normalizedCoords = fragCoord/iResolution.xy;
```

Now let's define some small offsets.

```js
vec2 redOffset = vec2(0.001, 0.002);
vec2 greenOffset = vec2(-0.002, 0.001);
vec2 blueOffset = vec2(0.003, 0.002);
```

Now that we have some offsets, we can just sample our texture with them. Assuming we have a texture sampler called `iChannel0`:

```js
float red = texture(iChannel0, normalizedCoords + redOffset).r;
float green = texture(iChannel0, normalizedCoords + greenOffset).g;
vec2 blueAlpha = texture(iChannel0, normalizedCoords + blueOffset).ba;
```

Using [swizzling](https://en.wikipedia.org/wiki/Swizzling_(computer_graphics)), or accessing only a specific component of a vector, we can easily only get the value we need. Notice that for the last channel, I use a vector 2 instead of a float, because of course, we need to get the alpha channel as well. We'll just use the blue offset to sample the alpha channel.

Now, we can join it all together.

```js
fragColor = vec4(red, green, blueAlpha);
```



## Edge Strengthing

So, we've constructed our output color with the offset channels. This is often times enough, but realisitically, you'll only see chromatic aberration near the very edges of images, and not so much the center.

To make this effect more realistic, we can simulate that.

We have the current normalized position in `normalizedCoords`. Now this ranges from 0 to 1, but with a bit of clever math we can get something cool.

First, let's shift our coordinates over.

```js
vec2 shiftedCoords = normalizedCoords - 0.5;
```

So now, the coordinates range from -0.5 to 0.5. We're close now, we just need to take the absolute value of the coordinates to get rid of that negative.

```js
shiftedCoords = abs(shiftedCoords);
```

Now, let's edit our previous texture sampling code.

```js
float red = texture(iChannel0, normalizedCoords + (shiftedCoords * redOffset)).r;
float green = texture(iChannel0, normalizedCoords + (shiftedCoords * greenOffset)).g;
vec2 blueAlpha = texture(iChannel0, normalizedCoords + (shiftedCoords * blueOffset)).ba;
```

So you see, the values range from 0.5 at the bottom left, to 0.5 at the top right. This means that in the center, the values are 0.0, or close to it. We're effectively reducing our offset by how close it is to the center. 

This means that the effect will only really be visible around the edges, which is exactly what we want.

However, it's probably not going to be that visible, as we've effectively halved it, seeing how we're multipling by at most, 0.5. So we can modify our absolute value line to increase it.

```js
shiftedCoords = abs(shiftedCoords) * 2.0;
```

Doubling it brings it back to the original strength, but you can increase this or decrease it however you want to tweak the strength.


## Full Program

```js
const float STRENGTH = 2.0;

void mainImage( out vec4 fragColor, in vec2 fragCoord )
{
    vec2 normalizedCoords = fragCoord/iResolution.xy;
    
    vec2 redOffset = vec2(0.001, 0.002);
    vec2 greenOffset = vec2(-0.002, 0.001);
    vec2 blueOffset = vec2(0.003, 0.002);
    
    vec2 shiftedCoords = normalizedCoords - 0.5;
    
    shiftedCoords = abs(shiftedCoords) * STRENGTH;
   
    float red = texture(iChannel0, normalizedCoords + (shiftedCoords * redOffset)).r;
    float green = texture(iChannel0, normalizedCoords + (shiftedCoords * greenOffset)).g;
    vec2 blueAlpha = texture(iChannel0, normalizedCoords + (shiftedCoords * blueOffset)).ba;

    fragColor = vec4(red, green, blueAlpha);
}
```

