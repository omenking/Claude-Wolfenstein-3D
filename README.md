# Claude-Wolfenstein-3D
Attempt to build Wolfenstein 3D Using Claude Sonnet 3.5

# V1

This initial setup includes:

A basic HTML structure with a canvas element.
CSS to center the canvas and set a black background.
JavaScript with:

Constants for game settings
A simple game map
Player position and angle
Canvas setup
A basic game loop
Placeholder functions for player movement and ray casting
A function to draw the player (as a yellow circle with a direction indicator)

When you run this, you should see a black screen with a yellow circle representing the player. The circle will have a line indicating the player's direction.
In the next steps, we'll implement player movement and basic ray casting. Let me know when you've tested this initial setup and are ready to move on to the next stage.

# V2

These changes introduce:

Keyboard state tracking (keys object and event listeners).
Player movement in the movePlayer function:

Forward/backward movement with Up/W and Down/S keys.
Rotation with Left/A and Right/D keys.


Basic collision detection with the isWall function.
Angle normalization to keep the player's angle between 0 and 2π.

Now, when you run this, you should be able to move the player around using the arrow keys or WASD. The player won't be able to move through walls.
The next step will be implementing basic ray casting to create the 3D effect. Let me know when you've tested this movement implementation and are ready to proceed to ray casting.

# v3

Key changes in this update:

We've implemented the castRay function to perform ray casting.
The castRays function now calls castRay for each ray.
We've removed the drawPlayer function as we're now rendering the 3D view instead of a top-down view.
The ray casting algorithm calculates the distance to walls and renders vertical strips based on this distance.
We've added fish-eye correction to prevent distortion at the edges of the view.
The color of the walls changes based on distance to create a basic depth effect.

When you run this code, you should see a basic 3D rendering of the walls. You can move around using the arrow keys or WASD, and the view should update accordingly.
This implementation provides a foundation for a Wolfenstein 3D-style renderer. From here, we can add more features like textures, a minimap, or more complex level designs.

# v4

The key changes are:

In the castRays function, we now draw the ceiling and floor before casting the rays:
javascriptCopy// Draw ceiling
ctx.fillStyle = '#383838';
ctx.fillRect(0, 0, SCREEN_WIDTH, SCREEN_HEIGHT / 2);

// Draw floor
ctx.fillStyle = '#707070';
ctx.fillRect(0, SCREEN_HEIGHT / 2, SCREEN_WIDTH, SCREEN_HEIGHT / 2);

The walls are now drawn on top of this floor and ceiling background.

Now when you run the game, you should see:

A dark gray ceiling at the top half of the screen
A lighter gray floor at the bottom half of the screen
Red walls that get darker with distance

This creates a more complete 3D effect, similar to the original Wolfenstein 3D. You can adjust the colors of the floor and ceiling by changing the hex color codes in the castRays function.

# v5

Key changes in this update:

We've added a createWallTexture function that generates a simple brick texture.
The castRay function now calculates the textureX coordinate based on where the ray hits the wall.
In the rendering part of castRay, we now use drawImage to render a strip of the wall texture instead of filling a solid color.
We've added a shading effect based on distance to give a sense of depth.

This implementation provides a basic textured wall rendering. The walls should now look like brick walls with some depth perception due to the shading.
You can modify the createWallTexture function to create different wall patterns or even load an image file for more complex textures.

# V6 

The main changes are:

We've added an <img> element to load the wall texture.
We've created a loadTexture function that returns a Promise to load the image.
We've added an init function that loads the texture and starts the game loop.
We've removed the createWallTexture function since we're now using an external image.
We've updated the castRay function to use the loaded texture image.

Make sure your wall_texture.webp file is in the same directory as your HTML file. The texture should be 64x64 pixels for best results, but the code will work with other sizes as well.
This approach allows you to easily swap out different textures by changing the image file, giving you more flexibility in the game's appearance.

# v7

