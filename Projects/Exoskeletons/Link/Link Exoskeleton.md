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

The revolute joint connecting Link1 and Link2 create a pinch point internal to the chain, as well as between Link2 and the Flex/Ex actuator external to the chain. The conceptual approach would be to add space to those areas such that at their maximum range of motion, there is still a gap between the linkages and minimize pinching. Additionally, the hips should retain the simplistic design approach w.r.t. overall geometry for ease of machining and applied tolerancing. Because Link2 is involved in both areas of concern, it should take the most priority in modification. Furthermore, both pinch points arise simultaneously during external rotation, observed below

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-153038.png" alt="Image 1" width="99%">
</div>

The new design approach shows the joint connections on either end of Link2 initially start parallel with the directions of the link connections they attach to. These parallel segments are then connected directly to one another, resulting in a zig-zag shape. The profile approach adds large amounts of space in the areas of concern, while still remaining simplistic in shape. By keeping the linear shape, the new design still offers means for easy machining and/or weight saving strategies. The shape works for internal rotation, however the profile must have enough space throughout the rest of the yaw motion.

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-153038.png" alt="Image 1" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-153038.png" alt="Image 1" width="99%">
</div>

The initial goals for the design were to maintain the same overall link lengths as those used in Mk.2, however retaining the fulling machined approach in order to be able to handle the torque requirements of the actuators. Because the hips were fully machined, weight optimization played a significant factor, where any weight savings strategies needed to comply with the material behavior of the components. The first design pass and analysis are as follows.

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-153038.png" alt="Image 1" width="99%">
</div>

Link1 static analysis, conducted similarly to that of Mk.2 is as follows:
- 80N continuous hGRF from peak Flex/Ex torque
- 65Nm remote peak Flex/Ex torque (x=43mm, y=-190mm)
- Link weight: 0.272 kg

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-153711.png" alt="Image 1" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-153739.png" alt="Image 1" width="49%">
  <img src="image-20240905-153803.png" alt="Image 1" width="49%">
</div>

Link1 dynamic impulse analysis was also analyzed:
- 1200N remote instantaneous vGRF (x=43mm, y=-190mm)

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-154716.png" alt="Image 1" width="49%">
  <img src="image-20240905-154736.png" alt="Image 1" width="49%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-154758.png" alt="Image 1" width="99%">
</div>

The impulse condition shows higher stress concentrations at the fixated proximal end, however the static condition shows slightly higher deformations from the loading conditions. pockets were extruded on both faces of the link in order to reduce overall weight conditions and provide the link with an overall double I beam cross section. However, I beams are optimized for cantilever loading that Link2 experiences the most, while the proximal link experiences more torsion loading. The pocketing/weight saving strategies do not have to be consistent across each link, and should instead reflect the loading scenarios each is anticipated to endure. Another approach was adjusting the pocket geometry on both sides of the link to have a cross configuration instead of the singular horizontal support.

- Link weight: 0.299 kg

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-161356.png" alt="Image 1" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-161548.png" alt="Image 1" width="49%">
  <img src="image-20240905-161606.png" alt="Image 1" width="49%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-161629.png" alt="Image 1" width="99%">
</div>

The same analysis was done with the cross bar design and pockets go through the entire structure

- Link weight: 0.269 kg

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-190134.png" alt="Image 1" width="49%">
  <img src="image-20240905-190159.png" alt="Image 1" width="49%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-190229.png" alt="Image 1" width="99%">
</div>

The pocketing strategy that extrudes through the component yields the best rigidity to weight ratio

Link2 static analysis, conducted similarly to that of Mk.2 is as follows:
- 80N continuous hGRF from peak Flex/Ex torque
- 65Nm remote peak Flex/Ex torque (x=0mm, y=-59mm)
- Link weight: 0.231 kg

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-192726.png" alt="Image 1" width="49%">
  <img src="image-20240905-192752.png" alt="Image 1" width="49%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-192837.png" alt="Image 1" width="99%">
</div>

Two Link assembly w/ respective hinge pins. The goal of this study is to understand the stress propagations proximal to the first hinge pin that ties the Ab/Ad Link and Link1 together in order to assess potential materials to use for the pins other than the 4340/D2 tool steel in the past. The yield stress of 4340 is very high and was chosen for this application, however it is difficult to machine and therefore increases cost, as well as introduces a rust and corrosion problem. The strongest corrosion resistant steel is 316L, with a yield strength of 205 MPa and fatigue strength of approximately 145 MPa.

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-203846.png" alt="Image 1" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-203919.png" alt="Image 1" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-203952.png" alt="Image 1" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-204022.png" alt="Image 1" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-204108.png" alt="Image 1" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20240905-204155.png" alt="Image 1" width="99%">
</div>

A secondary pass was done with the individual hip linkages in order to cut down on weight or improve stress propagations. There is no need for hip encoding specifically for the V1 pass of the device, which allows the hinge pins of the hip chain to be simplified down. Additionally, the material for the pins were changed from 4340 to 304/316 stainless steel for corrosion resistance and ease of machining. Link2 employs the use of a double I beam cross section given the cantilever behaviors is would experience during peak loading scenarios, however the high rigidity resulted in torsion stress concentrations across Link1. For a more uniform approach, Link 2 was altered to have a singular I beam cross section, all the while cutting away material. The analysis was conducted with the hip chain at its fullest internal rotation ROM to maximize the distance from the ab/ad link

Loading scenario:
- 1200 N vGRF
- 70 Nm peak torque applied by Flex/Ex
- 70 N hGRF generated by the Flex/Ex torque

All results shown in the Onshape FEA was verified with SW for consistency and accuracy.

<div style="display: flex; gap: 2%;">
  <img src="image-20241029-190031.png" alt="Image 1" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20241029-190055.png" alt="Image 1" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20241029-190131.png" alt="Image 1" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20241029-190433.png" alt="Image 1" width="99%">
</div>

The transition to a single I beam as well as altering the end curvature of Link1 to be conical rather than circular resulted in approximately 10 g reduced weight from the initial pass. The hip chain shown previously, minus the Ab/Ad link attachment, currently weighs 0.908 g.
  
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
  <img src="firsttestingsetup.png" alt="Image 1" width="75%">
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
  <img src="secondtestingsetup.png" alt="Image 1" width="99%">
</div>

After all testing conditions of the protocol passed, testing the EtherCAT communication chain was next. To accomplish this, a secondary EK1100 Beckhoff module was obtained and connected in series with the first, with the thigh link connected in the middle. This method provided the means to monitor both missed deadlines and working counter mismatches. This method also produced excellent results across all protocol tests without any missed deadlines in the communication chain for two protocol iterations.

<div style="display: flex; gap: 2%;">
  <img src="20250308_Link_02.jpg" alt="Image 1" width="99%">
</div>

The FEA provided in the thigh package review lacked critical details regarding its overall performance under high stress testing and needed to be reevaluated. The loading conditions are:
- 1200 N vGRF remote load (y=-1120mm, x=75mm)
- 4x M4 clamp bolts torqued to 4 Nm
- Largest thigh bar; largest height setting from hips to ground based on Mk.2 ranges

Other assumptions were also made for this FEA
- Clamp dimensions were adjusted to be flush with all four faces of the CF bar; does not reflect true clamp displacement due to gap spacing
- Fillets were added/adjusted across high stress concentration areas indicated in the previous FEA
- Uses a remote loaded mass rather than axial loading to account for the generated moment by the foot in a lateral closed chain system.

<div style="display: flex; gap: 2%;">
  <img src="image-20241213-152520.png" alt="Image 1" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20241213-143415.png" alt="Image 2" width="99%">
</div>

<div style="display: flex; gap: 2%;">
  <img src="image-20241213-143321.png" alt="Image 3" width="99%">
</div>

The loading conditions are:
- 1200 N vGRF remote load (y=-1120mm, x=75mm)
- 4x M4 clamp bolts torqued to 3 Nm
- 140 Nm load applied to hip (double peak to account for opposing torques from hip and knee)
- Largest thigh bar; largest height setting from hips to ground based on Mk.2 ranges

<div style="display: flex; gap: 2%;">
  <img src="image-20241213-142446.png" alt="Image 4" width="99%">
</div>

The goal for the internal wiring for the CF Thigh bar is to make two exact copies that can be used on either side of the exoskeleton, while making the orientation discrete to ensure the IMU remain proximal to the hip actuator. Due to the limited space of the actuator packages, the twitter logic and ethercat communication signals will be wired to their nearest terminal, and any wire crossing/twisting can occur within the thigh bar itself.

Here are all cables that run through the thigh:
- EtherCAT
- T+ is TxP
- T- is TXN
- R+ is RxP
- R- is RxN
- Logic Power
- 33V
- GND

Actuator Power
- 33V
- GND

While they are the same voltage, the logic and actuator power lines are kept separate from one another. The actuator power line travels straight through the thigh, while logic power and EtherCAT are terminated with an H4 IMU in series. The lengths of these wires are cut based on the minimum slack needed to effectively disassemble/reassemble the electrical inserts. For the actuator power, crimp two anderson powerpole connectors to the end, fasten to one of the electrical inserts, and feed the wire through the bar. There should be enough cable slack such that the electrical insert on the opposite end can be completely removed from the bar. Providing too much slack can introduce tangling of cables internally and pressing against the IMU board.

<div style="display: flex; gap: 2%;">
  <img src="image-20250211-204341.png" alt="Image 3" width="30%">
  <img src="image-20250211-211130.png" alt="Image 2" width="30%">
  <img src="image-20250211-212549.png" alt="Image 1" width="30%">
</div>

Focus attention to the orientations and polarity of the anderson powerpole connectors for either end of the bar as to ensure they are not the same. For the Ethercat communication, the T+, T-, R+, R- sequence should be consistent across all connections for the millmax connections. Note the flip in the EtherCAT signals on either side of the Twitter and IMU boards. There are two potential methods for mating the EtherCAT signals between slaves:

- Twit_TXP to IMU_TXP
- Twit_TXN to IMU_TXN
- Twit_RXP to IMU_RXP
- Twit_RXN to IMU_RXN

or

- Twit_TXP to IMU_RXP
- Twit_TXN to IMU_RXN
- Twit_RXP to IMU_TXP
- Twit_RXN to IMU_TXN

The first method is preferred for simplicity sake and matching the connector signals on the PCBs.
