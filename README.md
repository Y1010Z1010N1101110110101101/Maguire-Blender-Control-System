# Maguire-Style Gravimetric Batch Blender Control System (PLC)

An advanced, high-precision Industrial Automation solution developed in PLC to control and optimize a multi-component gravimetric batch blender, inspired by the industry-standard *Maguire (German brand)* blending systems. 

This project implements a fully automated, weight-and-percentage-based dosing, dispensing, and mixing sequence for up to *4 distinct material hoppers*, ensuring maximum recipe accuracy and process reliability.

---

# System Architecture & Process Flow

The system orchestrates a highly coordinated sequence divided into four main stages:

1. *Material Vacuum Loading (Suction Stage):* Automatically manages the pneumatic/vacuum suction to pull raw materials into *4 top-mounted receiver hoppers* positioned above the blender.
2. *Precision Gravimetric Dosing (Weighing Stage):* Dispenses materials sequentially from the hoppers into the internal weigh chamber based on user-defined recipe percentages and target weights.
3. *Homogeneous Mixing (Blending Stage):* Once the precise batch weight is met, pneumatic dump valves release the material into the mixing chamber where the blending cycle runs for a optimized duration.
4. *Discharge & Downstream Integration:* The fully blended batch is discharged to the bottom chamber/reservoir, ready to be drawn by the next production machine.

---

# Key Features & Control Logic

## Two-Stage Dosing Algorithm (Coarse & Fine Feed)
To eliminate material inertia and prevent weight overshoot (*Over-shoot Mitigation*), the PLC logic implements a smart two-stage dispensing mechanism for each of the 4 materials:
* *Coarse Feed (Fast Charging):* The pneumatic valve opens fully until the material weight reaches *80%* of its target recipe value.
* *Fine Feed (Trickle/Pulsed Dosing):* Upon hitting the 80% threshold, the PLC switches to a throttling/pulsed pneumatic valve control, feeding the material incrementally and slowly until exactly *100%* accuracy is achieved, before seamlessly moving to the next material.

## Pneumatic Valve Optimization
Utilizes dedicated digital outputs to control industrial pneumatic air valves for clean material shearing, precise dispensing, and chamber dumping, eliminating mechanical jamming.

## Recipe-Driven Control
Fully dynamic system driven by weights and percentages entered via the HMI/Control Panel, allowing the system to scale batch sizes automatically while maintaining perfect component ratios.

## Safety & Interlocking Logic
* Sequential interlocking: Second material will never dispense until first material is perfectly batched.
* Level sensor integration to prevent overfilling the mixing chamber or running the next machine dry.
