---
layout: project
title: Torque Wrench Design 
description: MATLAB, CAD, & ANSYS Project
technologies: [Autodesk Fusion, ANSYS, MATLAB]
image: /assets/images/radio-machine-cad.jpg
---



For my Mechanics of Materials class, MAE 3270, I was tasked with designing a 3/8" drive torque wrench rated for a torque of 600 lb f to meet the following specifications:

- The wrench must sustain a fully reversed torque of T = ±600 in-lbf for 10^6 cycles. 
- The strain guages, attatched 1 inch down the bar from the drive, must attain at least 1.0 mV/V output at the rated torque.
- There must be a safety factor of Xo = 4 for yield or brittle failure.
- There must be a safety factor of XK = 2 for crack growth from an assumed crack of depth 0.04 inches (1 mm).
- There must be a fatigue stress safety factor of XS = 1.5.
- The material must be a steel, aluminum or titanium alloy.

With the help of my partner, Erik Salamanca, ....

My contribution to the project was the CAD model, FEM analysis, parts of the hand calculations and the report writeup linked here (insert link here). We jointly wrote the MATLAB code, iterated on the dimensions of the bar of the torque wrench, and researched materials through ANSYS Granta EduPack, settling on 7075 Al T6 for its strength and ductility. We calculated that with a drive-end length L = 15", height b = 0.5", and width h = 0.8", a design made out of this material would satisfy all of the above requirements.

Using beam theory, our hand calculations state the following about our design:

Deflection at the load point is 0.21094 inches.
Max Stress is 11.25 ksi.
Strength Factor of Safety is 6.4267 (>4, satisfying Xo requirement).
Fracture Factor of Safety is 5.418. (>4, satisfying XK requirement).
Fatigue Factor of Safety is 2.3111.(>4, satisfying XS requirement).
Strain Gauge value is 1125 microstrain.
Voltage Output to input is 1.125mV/V (satisfying strain gauge output requirement).

Then, I created the CAD model using Autodesk Fusion, parametrized using the dimensions calculated previosuly. these dimensions are shown in the below images:
<img 
  src="{{ site.baseurl }}assets/images/TW CAD Top View.png" 
  alt="Top View"
  width="500">
  
<img 
  src="{{ site.baseurl }}assets/images/TW CAD Top-Front View.png" 
  alt="Top-Front View"
  width="500">

  <img 
  src="{{ site.baseurl }}assets/images/TW CAD Drive Zoom.png" 
  alt="Drive Zoom"
  width="500">

  <img 
  src="{{ site.baseurl }}assets/images/TW CAD Front Zoom.png" 
  alt="Front Zoom"
  width="500">

After finishing the CAD model, I imported the geometry as a STEP file into ANSYS, performing a static-structural analysis by clamping the drive with a zero-displacement condition and applying a 40-lb force to the end of the wrench as indicated in the below diagram:

Material: 7075 Al T6
Young’s Modulus: 10000000 psi
Poisson ratio: 0.325
Yield Stress: 72300 psi
KIC: 24200 psi
Fatigue Stress at 1e6 cycles: 26000 psi

After assigning the material 7075 Al T6 to the geometry and checking to see that the material properties were consistent with what we used in our MATLAB code, I solved the model for max normal and primary stresses, deflection, and elastic strains. 

Included below are images of the normal strain contours, max principal stress contours, and deflection:


To summarize the results of our analysis, we found that:
- The max deflection at the end is 0.31424 in, representing a 32.7 % difference to our hand calculations
- The strain gauges located on either side of the drive on both sides of the wrench would measure strains of 1041.5 and -1040.6 microstrain, which give percent differences of 7.71% and 7.78% respectively
- The max normal stress was affected by the mesh sizing around the filleted area, which represented a stress concentration that wasn't reflected in our hand calculations (since we didn't take the drive into account). With a mesh sizing of 0.06" at the drive and fillet, the max normal stress (not including the erroneous one caused by boundary condition misalignment above the fillet) was 22286 psi, corresponding to a factor of safety Xo = 3.54: too low! By iterating through several mesh sizing solutions, I found that sizing the fillet mesh at 0.1" did not significantly affect the geometry and gave a measurement of 17900 psi at the same location, corresponding to Xo = 4.03.
- An interesting thing to note here is that the stress used here is the stress in the z direction. In reality, it would be better to use the equivalent stress (von Mises) to calculate the factor of safety.
- Using strains measured at the strain gauge location from the FEM, 1041.5 and -1040.6 microstrain, we predict that the torque wrench sensitivity in mV/V would be about 1.04 mV/V.
  
Taking all of this into account, as well as the physical size of the object, my partner and I decided that the SGT-1LH/350-TY13 half bridge uniaxial strain gauge would be a good choice of product to choose to test our torque wrench.







