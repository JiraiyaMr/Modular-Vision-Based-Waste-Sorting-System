# Development Timeline

Translated from the dated comments in [Core/Src/main.c](../Core/Src/main.c), lines 16–24. These are the developer's historical notes, rather than dates inferred from Git upload history.

| Date | Recorded milestone | Source context |
| --- | --- | --- |
| 2024-10-19 | Added sorting tasks and USB communication. Nano-side data were read from the USB receive buffer. | sort_motor.c, sort_servo.c, UserRxBufferFS in usbd_cdc_if.c |
| 2024-10-23 | Successful integration test with the recognition algorithm. | Recorded in the main.c development log |
| 2024-10-24 | Added the conveyor transport task. | belt_motor.c |
| 2024-11-12 | Added automatic recentering, recorded as a change in sort_motor.h. | Original log wording; current control implementation is in sort_motor.c |
| 2024-11-24 | Added the laser distance-sensing task. | laser_distance.c |
| 2024-11-24 | Added the serial display; integration testing remained pending at that point. | Original log explicitly says testing was pending |
| 2025-02-15 | Added a PC-bound data-transmission component, recorded under sort_motor.c. | Historical note; current snapshot routing should be checked separately |
| 2025-02-28 | Successful laser-sensor control-board test. | Recorded in the main.c development log |

The timeline describes incremental integration of sensing, communication, transport, sorting, and user-interface functions. It does not establish a measured end-to-end sorting success rate.

