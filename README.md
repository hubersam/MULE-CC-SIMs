# NASA RASC-AL MULE-CC Simulations

From 2022 to 2023, I worked with a team of hard-working undergraduate aerospace engineering majors on a submission for the [NASA RASC-AL competition](https://rascal.nianet.org/). We won "Best Presentation", and the technical paper and livestream video can be found [here](https://rascal.nianet.org/2023-teams/) under the "Lunar Surface Transporter Vehicle Theme" from "Virginia Polytechnic Institute and State University". 

The theme was:
> Lunar Surface Transporter Vehicle

for which we had to:
> Develop a vehicle concept for offloading, moving, deploying, and supporting payloads on the lunar surface, up to the scale of habitats.

The "Multi-Use Lunar Environment Cargo Carrier (MULE-CC)" was our proposed vehicle, and this repository demonstrates the two simulations that I created for our submission.

# Simulation 1

The first simulation was created in Unreal Engine. It displays the south pole of the lunar surface with realistic lighting and and orbital positioning.

The landscape height data was taken from the [Lunar Orbital Laser Altimeter (LOLA) Satellite Data Archive](https://imbrium.mit.edu/BROWSE/LOLA_GDR/POLAR/SOUTH_POLE/). Since the focus of the project was almost directly on the lunar south pole, I used the -87.5 degree dataset (warning: it is large). This means that the actual amount of landscape in the simulation corresponds to a 2.5 degree change in latitude from the lunar south pole. The entire section is 150 square kilometers in area, and the in-engine version is to-scale.

In order to convert this grayscale image into vertex data for meshes, I used the experimental Geometry Script feature. Geometry Script allows you to build static meshes triangle by triangle, with each vertex and normal being specified by the user. The grayscale image was then converted into static meshes (tiled, since one giant mesh would cause a crash).

At this point, since these static meshes are saved in the engine, Nanite could be enabled for them, allowing for great level of detail. On top of this, to accurately simulate lighting data, Lumen was used. There was some odd behavior, but with the scale of the project and Lumen being so new, that was to be expected.

Once the tiles were placed to create the perception of one landscape, I added a large sphere for the Earth and a large directional light for the sun. The size of the Earth and the light intensity from the Sun is also to-scale.

To make sure that the positioning of the Sun and Earth were correct, I used NASA's SPICE Toolkit (which was used in blueprints from the MaxQ Spaceflight Plugin). This toolkit enables vector calculations from any desired reference body. I added a menu to specify the date, time, and rate of change of time. Therefore, you can set the simulation to any desired date and time and observe the relative positions of the Sun, Earth, and lit surfaces/shadows on the lunar surface. This could enable mission planning for the south pole lander.

This simulation also allows you to select to positions on the surface and calculate the straight-line distance. It can also calculate the required energy output of the lunar lander going from the first point to the second point. In addition, since the lunar lander can only drive on a small range of landscape inclination, the user can specify the safe inclination for the lander to drive on, and the simulation will show the areas that are safe. To top it off, the simulation will also allow you to pick two points and calculate the path for the lunar lander to take without driving on any unsafe inclination areas.

A demonstration can be seen below.



# Simulation 2

The second simulation, also created in Unreal Engine, was created for virtual reality (specifically for the Meta Quest Pro). The simulation allows you to get a to-scale 3D view of the vehicle. The user can manipulate the positioning of the forks, mast, legs, and wheels by using the joysticks and menu options. A demonstration can be seen below.



The actual projects themselves have not been uploaded yet due to size contraints. Once I find a reasonable way to upload all of the files without violating GitHub's maximum repository size, I will upload them.
