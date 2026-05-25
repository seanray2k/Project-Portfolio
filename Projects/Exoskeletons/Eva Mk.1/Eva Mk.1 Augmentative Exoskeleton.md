# Eva Mk.1 Augmentative Exoskeleton

## Introduction
Cleanup efforts at U.S. DOE tank farm sites have been ongoing since the mid 20th century and are
projected to continue past 2050 [1], with the ultimate goal of safe decommissioning of sites and disposal
of nuclear waste without contaminating the surrounding environment. The workers tasked with
completing this mission are exposed to significant radiological hazards as well as heavy manual labor, a
varied taskset, and extreme temperatures [2] (Figure 1). PPE is required to shield workers from radiation,
completely covering the body and providing breathing protection ranging from respirator masks to fully
self-contained breathing apparatuses (SCBAs) depending on the dose level of the work environment.
However, SCBAs are often cumbersome and, while providing excellent protection against contaminated
particulates, can be detrimental to the wearer’s biomechanics especially during dynamic and unstructured
movement. Working with this added mass increases fatigue, leading to an increased risk for acute and
chronic injuries.

As such, there is a strong desire to increase worker safety across sites. One field that is
increasingly being explored for this purpose is robotics, with some systems having been successfully
developed and deployed to sites [5]. Many of these robots are able to complete important exploration and
monitoring work [6], and some can operate in areas that are difficult to access by humans [7]. However,
these robots are usually designed for singular purposes, are limited in their ability to traverse uneven
terrain, and lack the decision making capabilities and dexterity to complete a full tank farm workday.
While robots can currently serve as useful tools, humans must complete the vast majority of work.

White standalone robots serve limited purposes, the technology can be applied to directly affect
worker safety in the form of wearable robots, or exoskeletons. Common industrial exoskeletons are
passive, utilizing unpowered mechanisms to assist specific repetitive movements (e.g. floor-to-waist
lifting, overhead manipulation tasks, working while leaning). These are usually effective at assisting
singular tasks, and many of these devices are currently being field tested due in part to the DOE Wearable
Robotics Program [8]. However, their usefulness is limited in unstructured work environments that
consist of numerous diverse tasks, and their assistance magnitude is restricted to the mechanical
properties of the passive elements. Furthermore, in situations that necessitate SCBAs, common
exoskeletons cannot structurally offload the added weight from the wearer.

## Previous Work
In order to bridge these gaps in the field, and in collaboration with Sandia National Labs (SNL), IHMC is
developing the powered hip-knee-ankle exoskeleton, Eva, with the purpose of offloading PPE and
assisting tasks common to tank farm work. The first prototype, or Eva Mk1 (Figure 2.a), featured sagittal
actuated degrees of freedom of the legs (i.e. hip and knee flexion/extension, ankle plantarflexion), as well
as a suite of onboard sensors for state estimation and control (i.e. IMUs on each linkage, encoders at each
joint, pressure sensitive insoles). It was directly built around a commercial off-the-shelf (COTS) SCBA
harness, and featured height adjustability in the form of modular carbon fiber linkages.

Eva Mk.1 served as a testbed for task-agnostic gravity compensation control designed to offload
the weight of the exoskeleton and SCBA from the user regardless of posture [9], [10], task-specific
controllers designed to assist specific movements common to tank farm work as shown in Figure 2.b (e.g.
pushing/pulling, squatting/lifting, and walking), and a machine-learning (ML) based task classification
system to recognize and transition between task specific controllers as shown in Figure 2.c [11]. It also
allowed for testing of numerous body interfacing methods and biological joint collocation strategies.
Much of this work has been presented at various robotics and DOE conferences throughout the last few
years.

These developments were important steps on the path toward realizing a site-fieldable load
carriage exoskeleton prototype and led to important design improvements to increase the technology
readiness level (TRL) of Eva. In this paper, we detail these improvements in the development of the next
generation Eva Mk2 exoskeleton, some initial demonstrations of new capabilities, as well as future work
to further increase site applicability.

Supplementary material regarding the performance and collected data with the Eva Mk.1 exoskeleton can be found in [Li et. all]() and [Winship et. all]()
