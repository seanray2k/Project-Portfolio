# Link Augmentative Exoskeleton

## Introduction
The Eva Mk.2 exoskeleton was a great device with high potential for on-site deployment assisting with labor intensive tasks. However, further human piloting and experimentations, the following conclusions became apparent: Mk.2 lacked in usage for non-load carriage tasks, the SCBA harness systems are not as widespread in hazardous environments as they once were, and there little confidence in the adoption of the technology that the likelihood of site-use approval was low. At the time, there was not a catch-all exoskeleton device designed to assist users over wide ranges of tasks, and developing such a device requires extensive time, resources, funding, and experimental validation. Instead, the focus was shifted such the structure should easily morph to the requirements of the customer and use case that warrants physical assistance.

## The Device
<div style="display: flex; gap: 2%;">
  <img src="Sean Link (1).png" alt="Image 1" width="99%">
</div>

Link is an assistive device system that can be configured for a wide range of purposes to address this problem. Because there is no “catch-all” exoskeleton device, the approach was changed to where the hardware is configured based on the task. At its core, Link is a high-power 2 DoF hip exoskeleton with add-ons including:

- knee flexion/extension
- ankle plantarflexion (exploring both passive and active options)
- upper body joints driven by lighweight cable-based systems

<div style="display: flex; gap: 2%;">
  <img src="2025_Link_Intro_v5-HighBitrate.webp" alt="Image 1" width="99%">
</div>

Different controls policies are applied for each sensed configuration and based on a wide ranging dataset of biomechanical measures from common manual materials handling motions and ambulation styles. This is also paired with a transparency mode that will allow the user to move freely in the device with or without extra assistance.

Electrically, the system is controlled by an NVIDIA Jetson computer and functions off of custom LiPo batteries, capable of powering the suit at it’s full configuration (upper body and lower body) for approximately one hour. The user will have access to an onboard operational user interface (OUI) style controller, and control various aspects of device operation, including but not limited to toggling active assistance, modulating and metering assistance magnitudes, and monitoring device status. The manual settings of the device (lengths of the bars, etc.) will be handled automatically without altering parameters on the computer.

<div style="display: flex; gap: 2%;">
  <img src="20250308_Sean_All_HighBitrate.webp" alt="Image 1" width="99%">
</div>

## Contributions
The Link exoskeleton provided the opportunity to deploy an assistive device using the custom brushless cycloidal actuators optimized for this particular application detailed in my graduate thesis. Synonymously with the V2 actuation development and modifications, additional effort was required to package it with a dedicated motor controller and in-series electrical harnessing as part of a singular embedded packaged system, capable of easy swapping/replacement to minimize servicing downtime. These actuation packages were linked together using a locking mechanism with modular thigh structures and integrated electronics to reduce visible external wiring. Muliple revisions were applied to the passive hip chain structure introduced in the Mk. 2 exoskeleton and optimized for Link.

### The Actuators
The V2 brushless cycloid actuators are the next iteration in part of the design progression of the V1 prototype, explained in greater detail [here](https://github.com/seanray2k/Project-Portfolio/blob/main/Prototypes/Actuators/Custom%20Actuators/Cycloidal%20Actuator%20Research/17%3A1%20Cycloidal%20Actuator%20for%20Exoskeletal%20Research.md). Alterations transitioning into V2 included surface finishing and anodization, threading and profile modifications to the external housing for embedding with the rest of the mechanical structure, and changes to the applied tolerances to part drawings to improve transmission quality as well as eliminate unnecessary manufacturing costs.

### The Hips

The linkage based design for the hip chain developed for the Eva Mk.2 device was readapted for the Link device. The mechanical behaviors were observed and various issues were acknowledged and needed revisiting. The hard stop on the second linkage engages firstly in the chain during external rotation, and motion is compensated for by the first linkage and the flexion/extension linkage. The first linkage hard stop engages 4 degrees after the second, accounting for the full true external range of rotation. Additionally, the hard stop range of the second linkage could not be expanded to be the same as the first (such that they would engage at the same time) due to the existing hard stop preventing the second linkage from reaching a singularity point and potentially collapse the hips inward towards the user. 

Expanding the link dimensions would counter the singularity issue, however this would negatively impact users in the lower percentile range, whos lower hip depth from the gluteal region already forces the first linkage to its external hard stop and limits overall range of motion. Vice versa would apply for larger users if the profiles shrank. A potential avenue would be to explore maintaining the current positions of the passive joints in the chain, but alter the profile geometry between the joints in order to change the vectors of internal forces during loading. This could be another method for adjusting where the singularity points between joints occur.

With power applied to the system and gravity compensation active, the torques generated by both the abduction/adduction and flexion/extension DoFs (same direction) put the hip links in a constant state of torsion. When the user flexes their leg upward and performs floating internal/external motion, the torque application from both hip actuators are acting in opposing directions. During floating external rotation, the opposing torques create a “collapsing” behavior, where the links in the chain quickly settle into their full rotation positions. This behavior has been observed during floating internal/external rotation, and not during standard vertical internal/external motion. This could be addressed by having tracking across the hip links and tuning the applied torques across abduction/adduction, however this does introduce a pinch point and cause the user injury.

### The Legs

The hip flexion/extension ROM downward featured the modular design aspect that would inspire future linkage additions on the upper and lower body portions of the device going forward. The methodology was to design standalone actuator packages(cycloidal actuator unit, input and output encoding, embedded motor controller, and wire pathing) configured to respective joint DoFs by external ROM hardstops, which could be linked together with a lightweight carbon fiber segment whose lengths are configured based on the anatomical measurements of the users estimated joint centers. The base system (hip abduction/adduction and flexion/extension) could ideally be worn by any user after making the necessary soft intefacing adjustments, and the device would then be tailored to both the users physical stature as well as the degree of joint assistance desired.

<div style="display: flex; gap: 2%;">
  <img src="modulardesign.png" alt="Image 1" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="hipconfig.png" alt="Image 1" width="49%">
  <img src="hipkneeconfig.png" alt="Image 2" width="49%">
</div>

Interconnecting the physical modules and communication slaves required a physical connection method that mandated the following requirements. The physical connection needed to be robust to the cyclic moment loading and impact forces with various gait patterns, while being simple in its attachment method to not be confusing to the user who may not have mechanical experience. Both power and EtherCAT communication through each in-line connection needed a high mating cycle with freqency ratings in order to withstand the vibrations of the actuator transmissions, and be restricted to specific mating orientations.

This many restrictions on an electrical connection limited available commerical options within an acceptable form factor. Instead, a custom connection was implemented. For the lower logic power and communication lines, an array of spring-loaded pogo pins (Mill-Max) were used within a concave receptical for assistied positioning. These connections possessed a high frequency rating within configurable housings for a compact arrangement. For actuator power, friction-based powerpole connections (Anderson) were rated for the 33V supply and higher amperage. Because the actuator power runs in series through each motor controller, the anderson connectors were kept together and assimilated to the side proximal to these solder joints. Additionally, powerpole connectors feature dovetail connections for holding multiple contacts together, whose configurable orientations create discrete mating patterns which restrict the orientation which the carbon fiber bar is inserted. This becomes important given that each bar contains a dedicated IMU, and by keeping the IMU proximal to the hip connection side, the sensor can retain the same direction and orientation regardless of bar length and without having to be reconfigured in software. 

<div style="display: flex; gap: 2%;">
  <img src="actuatortransp.png" alt="Image 1" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="thightransp.png" alt="Image 1" width="99%">
</div>

For the mechanical connection, I opted for a high surface area friction clasp secured with four screws. Stock carbon fiber tubing has loose thickness and perpendicularity tolerances, and the connection interface needed to compensate for this. The counterbored holes were left oversized to account for skewed alignment during tightening. Since the rectangular geometry introduces vertices subject to higher stress concentrations and not suitable for compression loading, each end of a bar features an epoxied aluminum insert that strengthens the profile internally when tightening down the clasp. 

Durability testing and first pass connectivity quality of the friction clasp was carried out with the printed mockup of the thigh link in order to assess the performance of the pogo pin connectors used in the custom electrical connections. The first pass was meant to specifically tested the connectivity of the connector as a whole with a constant signal, with the end goal testing using EtherCAT communication signals and measure any discrepancies. The testing protocol followed for this test can be found [here](https://github.com/seanray2k/Project-Portfolio/blob/main/Projects/Exoskeletons/Link/Link%20Attachment%20Testing%20Protocol.pdf)

Only one electrical connection spanning the chain of spring pins was tested for the first pass, while the final test will span the connectivity of four connections, arranged across the four corners of the 8 pin arrangement in order to exaggerate any deflection generated by moment loading. The signal was generated using a handheld multimeter, with each probe attached to the input and output of the connection chain. The probes rest on plastic pads to insulate from the optical table, but further insulation will be required for future testing. The screws have specified rested seating torques for securing the clamps onto the carbon fiber segment, however the plastic shrouds provided limitations to the extent the bolts were tightened. The clamp was tightened evenly to ensure an even interface. This was validated by hand pulling the shrouds by hand and ensuring there was no slip.

<div style="display: flex; gap: 2%;">
  <img src="firsttestingsetup.png" alt="Image 1" width="99%">
</div>

The individual testing procedures were followed in the order listed in the protocol:
- Compression/Tension Forces - No signal loss during constant or cyclic applications
- Waving/Shaking - No signal loss (limited by human frequency)
- Vertical/Horizontal Bashing - No signal loss during the vertical bashing test (repeated 5 times); No signal loss for the first two horizontal bashes, however the third caused the plastic clamping interface to fracture and resulted in loss of clamping pressure and signal loss.

<div style="display: flex; gap: 2%;">
  <img src="firsttestingfracture.png" alt="Image 1" width="99%">
</div>

New shrouds needed to be reprinted for testing to proceed. The preliminary results showed the plastic structure is the limiting factor for this testing, and the general signal generated through the link was maintained through the more rigorous tests before fracture. 

Additional trials were performed using two more methods: a sinusoid signal supplied by a function generator and EtherCAT communication chain. For each method, the same testing protocol was followed, with more wires soldered in place on either side of the thigh link where necessary for communication. For the function generator, a probe was attached to one side with an oscilloscope on the opposite measuring the same signal and monitoring any dropouts during the testing protocol. The signal supplied was set to 500 Hz to simulate the communication frequency of EtherCAT. 

<div style="display: flex; gap: 2%;">
  <img src="secondtestingsetup" alt="Image 1" width="99%">
</div>

After all testing conditions of the protocol passed, testing the EtherCAT communication chain was next. To accomplish this, a secondary EK1100 Beckhoff module was obtained and connected in series with the first, with the thigh link connected in the middle. This method provided the means to monitor both missed deadlines and working counter mismatches. This method also produced excellent results across all protocol tests without any missed deadlines in the communication chain for two protocol iterations.

<div style="display: flex; gap: 2%;">
  <img src="20250308_Link_02.jpg" alt="Image 1" width="99%">
</div>
