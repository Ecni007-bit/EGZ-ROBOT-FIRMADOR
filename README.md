# EGZ Robot Firmador

**Robotics reverse engineering · Embedded integration · Experimental validation**

I investigated a three-axis robotic drawing system to understand its actuator control and homing behavior. I identified the axes, characterized the stepper motors, and built an ESP32-S3 bench setup that moved the left arm using half-step commands.

**Edmundo López Jaramillo · EGZ Engineering Integration & Automation**

## Engineering challenge

Recovering useful behavior from an existing electromechanical device requires separating observations from assumptions. My work combines electrical measurement, actuator identification, controlled motion experiments, and investigation of the original controller's sensor signals.

## What I verified on the bench

| Experiment | Observed result | What it establishes |
| --- | --- | --- |
| Actuator mapping | J1 lifts and lowers the pen platform, J2 drives the right arm, and J3 drives the left arm. | A working axis map for subsequent experiments. |
| Stepper characterization | Five-wire motors; approximately 15.5 Ω from common to a phase and 30–31 Ω between phases. | Electrical characterization to guide bench integration. |
| Motor control | A XIAO ESP32-S3, 74HC595 shift register, and ULN2003 driver moved J3 with half-step commands. | Bench motion of one axis with an external controller. |
| Homing investigation | Bursts were observed on J8 pin 3 while the original controller returned to home. | A measured signal worth investigating further. |

## Validation status

Reliable home detection, coordinated control of all three axes, and calibrated drawing motion remain in development. Pulse silence alone does not establish home: loss of sensor power or a disconnected signal can also produce silence.

[Read the bench evidence and validation status](docs/VALIDACION.md) — detailed notes in Spanish.

## My engineering contribution

- Characterized an unfamiliar electromechanical system through measurements and controlled experiments.
- Integrated a microcontroller with external motor-control components.
- Distinguished axis-level bench results from complete robotic-system validation.
- Documented uncertainty and identified the next experiments needed for dependable operation.

This project demonstrates embedded debugging, hardware-software integration, motor-control experimentation, and engineering documentation.

## Next validation milestones

1. Establish repeatable electrical and mechanical criteria for the home position.
2. Validate each axis independently across its usable motion range.
3. Develop coordinated motion and calibrate drawing geometry and pen lift.
4. Record repeatability and failure behavior before broader demonstrations.

## Public repository scope

This repository publishes selected engineering observations and validation notes. Firmware, internal tooling, detailed implementation, and proprietary development files are privately maintained. There is no public software installation or runnable release in this repository.

[Explore my software and engineering portfolio](https://github.com/Ecni007-bit) · [Contact me on LinkedIn](https://www.linkedin.com/in/edmundo-l%C3%B3pez-jaramillo-0b207b145/)
