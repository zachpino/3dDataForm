### Closest Point Walker

![Closest Point Walker in Action](cpwalker.gif.gif)

Many parametric models, especially those attempting to minimize material use or create scaffolding, require a designer to find sets of points that are close to one another. Just like in biological growth, the shortest distance between a body and its nutrient will provide the sturdiest foundation.

This Grasshopper definition takes a movable target point and creates links between it and a controllable number of nearest points.

- Draw a grid
- Draw a controllable point
- Calculate the distance between the control point and all grid points
- Sort the points by their distances
- Cut the list of points to the desired number
- Draw a connecting line between the control point and its near neightbors

[Download the definition](closest_points_walker.gh)

![closest point walker](closestdistance.PNG)
