# EGZ Robot Firmador

I reverse-engineered a three-axis robotic drawing system to understand its motor control and homing behavior. I identified the three axes and built an ESP32-S3 bench setup that moved the left arm with half-step commands.

## What I verified on the bench

| Experiment | Result |
| --- | --- |
| Actuator mapping | J1 lifts and lowers the pen platform, J2 drives the right arm, and J3 drives the left arm. |
| Stepper characterization | All three motors have five wires. I measured about 15.5 Ω from common to each phase and about 30–31 Ω between phases. |
| Motor control | The XIAO ESP32-S3 drove J3 through a 74HC595 shift register and a ULN2003 driver. |
| Sensor activity | I observed bursts on J8 pin 3 during the original controller's return to home. Their timing helps narrow down what to measure next. |

The embedded sketches capture sensor activity for diagnostics. The electrical condition for a reliable home position and coordinated control of all three axes still need validation. Loss of sensor power or a disconnected line can also cause pulse silence.

## Explore the project

- [Bench evidence and validation status](docs/VALIDACION.md)
- [Connector map](hardware/PINOUT.md) and [half-step sequence](docs/MOVIMIENTOS.md)
- [Homing signal observations](docs/SENSORES_HOME.md) and [experimental ESP32-S3 sketches](firmware/README.md)
- [Summarized measurements](data/mediciones_resumidas.csv) and [Python analysis tools](tools/README.md)
- [Bench precautions](docs/SEGURIDAD.md) and [next experiments](docs/ROADMAP.md)

## Run the offline tools

Use Python 3.10 or later. The simulator prints the phase sequence without accessing hardware. The unit tests use synthetic CSV fixtures.

```sh
python3 tools/stepper_sequence.py --axis J3 --direction F --steps 8
python3 tools/analyze_sensor_csv.py --help
python3 -m unittest discover -s tests -v
```

**Edmundo López Jaramillo · EGZ** · [LinkedIn](https://www.linkedin.com/in/edmundo-l%C3%B3pez-jaramillo-0b207b145/)
