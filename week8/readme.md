### Project Time!

Complete [some tutorials](http://formularch.blogspot.com) to bolster your Grasshopper toolkit. Then, try to tackle the [class briefs](../week7/homework.md) according to the following tips.


-----

ID + JC

> Fitness : How can a set of arbitrary 2d children shapes best fit within another parent shape?

> Genome : Several sliders determining the orientation and position of the children shapes.

##### Walkthrough
- Make some shapes in Rhino that can fit tightly inside another
- Reference those in one *curve* param each
- Use the *move* node, with a *vectorxyz* node, to allow the children objects to move
- Use the *rotate (GAP)* node to allow the children to rotate based on a plane centered on their *area* centroids. Convert a slider to *radians*!
- Use the *curve | curve* intersect node to determine how much shared area there is between all of the children shapes (many of these will be needed to intersect each child with their siblings. These are bad intersections -- overlapping geometries.
- Use the *curve | curve* intersect node to determine how much shared area there is between each child and the parent shape . These are positive intersections -- the pieces fit within the parent!
- Subtract the negative intersection *area* from the positive intersection *area*

> [An alternate take](http://www.designcoding.net/packing-objects-with-galapagos/)

-----

MH
> Simulation Objective : How path does gas take when subjected to turbulence within a volume?

#### Walkthrough
- *Populate3D* a volume with random particles
- Apply some forces to those points like *vortex* or *unary force*  
- Use *CollideSrf* or *CollideMesh* to keep the particles with
- Connect the forces to the *Kangaroo* force input, along with the necessary *timer* and *toggle*
- Use a *trail* node to visualize the path the gas is flowing along

-----

BM

> Fitness : An object should be fully illuminated, and a nearby region should be fully shaded -- what geometry should surround a omnidirectional light source to produce this outcome?

> Genome : Position of points that define a set of diffuse and reflective surface

#### Walkthrough
- Model the scenario with simple shapes
- Model the diffuser with a Grasshopper *revolution* or other simple surfacing techniques
- *Mesh brep* to convert the Rhino objects to meshes
- Use *Mesh Shadow*, *Occlusion*, and *Exposure* to determine light interactions, and do calculations based on the *area* of the intersections between the light rays and the meshes to feed Galapagos 

-----

MC

> Data Form Logic : How does a mesh of the human body deform when subjected to data about food intake?

#### Walkthrough
- *Construct Points* to serve as attractors/repulsors
- *Deconstruct Mesh* on an imported mesh to get the vertices
- Find n *closest points* of the mesh to the attractor/repulsor points
- Find the direction using *vector2pt* between the attractor/repulsor point and the closest mesh vertex points
- Set an *amplitude* on that vector, with a slider for now -- to be replaced by data!
- Use the *move* node to shift the closest points away from the attractor/repulsor points based on the amplitude vector.
- *Replace items* of the mesh vertices list, adding in the moved points at the indices determined by the closest points node.
- *Construct mesh* with the newly replaced vertices, combined with the original faces

[meshdeform](meshdeform.gh)

-----

TK

> Fitness : Create a spinning top form with as much volume as possible, that will stay upright for the maximal amount of time. [This site](http://www.angelfire.com/folk/bobrian/topprinciplespin/spinprinciples.htm) has some formal guidelines for *top* performance.

> Genome : Many sliders determining how the top's side profile is designed.

#### Walkthrough
- *Construct Point* many times to define the side of a top. These should have flexible sliders for x, but each should be specifically placed for y (evenly spaced?)
- *Move* each of those points based on a slider and a *unit x* node
- Draw a *polyline* through all the points
- Create a *Revolution* surface with the polyline and a new *line sdl* axis
- *Cap* the surface
- Check its *volume*
- *Rotate (GAP)* the top capped surface to the angle that it should still spin stably (ie 30 degrees)
- *BREP | Plane Intersection* with the *xy plane* will show where the surface collides with the ground
- Take the *area* of that intersection, and *subtract* it from the *volume* determined above

-----

AS

> Data Form Logic : How can a footprint profile, and a 3-dimensional foot form, be expressed in a minimal amount of data points? 

#### Walkthrough
- Use a set of *construct points* moved away from some datum point (the heel extreme point?) 
- Use *interpolate* to draw a curve through the points
- Do the same for various meaningful cross sections and *loft* through the curves
- *Mesh brep* to convert to *cap*ped, loft into a closed mesh
- Install [Weaverbird tools](http://www.giuliopiacentino.com/weaverbird/) and smooth the resulting mesh with *catmull clark* subdivision node

----

UM

> Simulation Objective : How can we fold paper digitally?

#### Walkthrough

- Draw a folding patter with Rhino polylines
- Separate the folds that should fold up (valleys) from those that fold down (mountains)
- Use the `mesh polyline` command in Rhino to create the piece of paper with mesh edges where foldlines are
- Connect the *origami* node in Grasshopper to the imported mesh and two sets of curves.
- Sliders connect to set final fold state, and the position of the fold for interactive motion
- Set up *Kangaroo* with a *toggle* and a *timer* and the origami force object
- Add an anchor *construct point* if desired to hold the paper in place

[origami.gh](origami.gh)

-----

(Y)ML

> Fitness : What planar shape can fly highest and most stably given four doward thrust vectors (props)?

> Genome : Many sliders determining the profile and position/strength of the thrust vectors

#### Walkthrough

- Take a look at [this example](prop.3dm) and its simulation [grasshopper file](prop.gh) to get started with simulating flight.
- Manipulate the mesh to see how a deformed object flies to generate some rules to design around
