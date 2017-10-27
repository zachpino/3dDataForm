### Homework for 11/3 · Heightfields

In preparation for an introductory CNC exercise, please watch this [video tutorial](https://www.youtube.com/watch?v=ym_jI0BSD6M), and replicate it.

Then, make the following additions...

- Add *Deconstruct Point* in order to get *x,y,z* values from the *RecGrid* points
- Add *Construct Points* and attach the *x* and *y* outputs from above. This recreates the grid of points
- Attach your *Image Sampler* output to *z*, to give a 3rd dimension to the grid of points
- Attach the *construct point* made above to a *delaunay mesh* node, and *flatten* the input to produce a mesh deformed by the image
- You may want to introduce some math, such as a *division* or *subtraction* node, between the *Image Sampler* and the *z* input in order to flatten the panel to a reasonable height
- Play with different images, and different Image Sampler settings such as the channel of interest, to attain an unusually textured 3D panel

The final panel should fit within a 12" x 12" x 4" region.
