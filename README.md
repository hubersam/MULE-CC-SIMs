# NASA RASC-AL MULE-CC Simulations

From 2022 to 2023, I worked with a team of hard-working undergraduate aerospace engineering majors on a submission for the [NASA RASC-AL competition](https://rascal.nianet.org/). We won "Best Presentation", and the technical paper and livestream video can be found [here](https://rascal.nianet.org/2023-teams/) under the "Lunar Surface Transporter Vehicle Theme" from "Virginia Polytechnic Institute and State University". 

The theme was:
> Lunar Surface Transporter Vehicle

for which we had to:
> Develop a vehicle concept for offloading, moving, deploying, and supporting payloads on the lunar surface, up to the scale of habitats.

The "Multi-Use Lunar Environment Cargo Carrier (MULE-CC)" was our proposed vehicle, and this repository demonstrates my contributions to our submission.

# Proposal Video

The proposal video was created using the first simulation (described in the next section) in Unreal Engine. You can view the video here:

[![Video](https://img.youtube.com/vi/h5w4Ln8MAA0/0.jpg)](https://www.youtube.com/watch?v=h5w4Ln8MAA0)

# Simulation 1

The first simulation was created in Unreal Engine. It displays the south pole of the lunar surface with realistic lighting and orbital positioning.

The landscape height data was taken from the [Lunar Orbital Laser Altimeter (LOLA) Satellite Data Archive](https://imbrium.mit.edu/BROWSE/LOLA_GDR/POLAR/SOUTH_POLE/). Since the focus of the project was almost directly on the lunar south pole, I used the -87.5&deg; dataset (warning: it is large). This means that the actual amount of landscape in the simulation corresponds to a 2.5&deg; change in latitude from the lunar south pole. The entire section is 150 square kilometers in area, and the in-engine version is to-scale.

In order to convert this grayscale image into vertex data for meshes, I used the experimental Geometry Script feature. Geometry Script allows you to build static meshes triangle by triangle, with each vertex's location being specified by the user. The grayscale image was then converted into static meshes (tiled, since one giant mesh would cause a crash).

At this point, since these static meshes are saved in the engine, Nanite could be enabled for them, allowing for great level of detail. On top of this, to accurately simulate lighting data, Lumen was used. There was some odd behavior, but with the scale of the project and Lumen being so new, that was to be expected.

Once the tiles were placed to create the perception of one landscape, I added a large sphere for the Earth and a large directional light for the sun. The size of the Earth and the light intensity from the Sun is also to-scale.

To make sure that the positioning of the Sun and Earth were correct, I used NASA's SPICE Toolkit (which was used in blueprints from the MaxQ Spaceflight Plugin). This toolkit enables vector calculations from any desired reference body. I added a menu to specify the date, time, and rate of change of time. Therefore, you can set the simulation to any desired date and time and observe the relative positions of the Sun, Earth, and lit surfaces/shadows on the lunar surface. This could enable mission planning for the south pole lander.

This simulation also allows you to select two positions on the surface and calculate the straight-line distance, as well as the required energy output of the lunar lander going from the first point to the second point. In addition, since the lunar lander can only drive on a small range of landscape inclination, the user can specify the safe inclination for the lander to drive on, and the simulation will show the areas that are safe. To top it off, the simulation will also allow you to pick two points and calculate the path for the lunar lander to take without driving on any unsafe inclination areas.

A couple demonstrations can be seen below.

https://github.com/hubersam/NASA_RASC-AL_MULE-CC_SIMs/assets/103780625/6b805e56-b917-4cc7-9973-5de9ca4e9f87

https://github.com/hubersam/NASA_RASC-AL_MULE-CC_SIMs/assets/103780625/2c558166-b7b1-4b79-a111-7a335e1f1f26

# Simulation 2

The second simulation, also created in Unreal Engine, was created for virtual reality (specifically for the Meta Quest Pro). The simulation allows you to get a to-scale 3D view of the vehicle. The user can manipulate the positioning of the forks, mast, legs, and wheels by using the joysticks and menu options. A demonstration can be seen below.

https://github.com/hubersam/NASA_RASC-AL_MULE-CC_SIMs/assets/103780625/b7b72d4a-ef4c-4b0b-87f2-3c8e8f23346f

The actual projects themselves have not been uploaded yet due to size contraints. Once I find a reasonable way to upload all of the files without violating GitHub's maximum repository size, I will upload them.

# MULE-CC Model

As a part of the capstone, we had to create a small replica model of the proposed lunar roving vehicle. The purpose of this model was not to replicate the mechanisms that would be on the proposed vehicle, but rather to measure how the wheels would interact with the lunar regolith at different inclines. Therefore, we used a large wooden ramp and some sand at different incline angles to determine the amount of slip that would affect the wheels with varying weights.

The vehicle was made out of materials that could easily be purchased online and assembled by members of the team. I was personally responsible for wiring the electrical components, programming the Arduino, and creating an iOS application that would communicate with a Bluetooth module to start and stop the motors.

Here are a few videos of our first prototype:

https://github.com/hubersam/NASA_RASC-AL_MULE-CC_SIMs/assets/103780625/2c2e0675-c6b1-45aa-95d6-3890964049a6

https://github.com/hubersam/NASA_RASC-AL_MULE-CC_SIMs/assets/103780625/e2f1a79d-d98e-43b4-a776-dd80a24e1a3b

This was not the final product; after these test runs, the motors were swapped out for stronger ones. Additionally, the electrical components on the top were placed into a wooden box that was seated on top of the PVC structure and reorganized. The wooden box had a flap on top to access the inner electrical components. The top of the flap had a wooden pole such that gym plates could be placed on top to vary the weight of the vehicle.
