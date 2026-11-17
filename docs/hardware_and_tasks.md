# Hardware and Task Map

## Configuration recorded in source

| Item | Recorded configuration |
| --- | --- |
| MCU | STM32F407IG in Keil; STM32F407IGHx in Dustbin.ioc |
| System clock | 168 MHz in Dustbin.ioc; 12 MHz external oscillator |
| OS | FreeRTOS with CMSIS-RTOS wrappers |
| CAN | CAN1; configuration approximately 1 Mbit/s |
| Conveyor feedback | CAN IDs 0x201, 0x202, 0x203 |
| Rotary sorting feedback | CAN ID 0x205; GM6020-named output interface |
| Release servo | TIM1 channel 1 PWM |
| Distance sensor | USART6 reception in laser_distance.c |
| Serial screen | USART1 output via usart_printf() |
| Compression actuator | Emm V5 position-control interface |

Motor models, mechanics, power supplies, gear ratios, physical connector assignments, and sensor distance units must be matched to the actual prototype. CAN identifier names alone are not a complete bill of materials.

## Tasks created by the archived startup

| Task | Function | Timing visible in its body |
| --- | --- | --- |
| defaultTask | Calls USB device initialization, then idles | osDelay(1) |
| sort_task | Category handling and rotary-sorter control | osDelay(2) |
| servo_task | Servo release and display notification | osDelay(2), plus 1500 / 1000 tick waits during release |
| belt_task | Conveyor PID and transport logic | osDelay(2) |
| pc_task | Framed USB receive processing | osDelay(10) |
| laser_task | Distance reception | Blocking UART receive, then osDelay(2) |
| compress_task | Repeated actuator motion and feedback | Busy waits and HAL_Delay(2000) inside control |

These delays are scheduling requests, not measured execution periods. LCD_task is present in source but is not created in MX_FREERTOS_Init().

USB initialization appears both before the scheduler in main.c and in StartDefaultTask(). The laser task shares the PC task handle variable in the archived startup; see the snapshot notes.

