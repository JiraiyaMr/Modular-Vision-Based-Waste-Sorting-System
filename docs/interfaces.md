# Communication and Category Mapping

## Host-to-controller path

The sorting task reads UserRxBufferFS[0]. The USB CDC receive callback also copies the first receive-buffer byte into buf, which the servo task checks.

| ASCII command | Meaning used by display counters |
| --- | --- |
| '1' | Recyclable waste |
| '2' | Kitchen / food waste |
| '3' | Hazardous waste |
| '4' | Other waste |

Category names are evidenced by the strings in Application/usart_screen.c. They are distinct from the serial display's separate page identifiers.

## Embedded actuation

- Conveyor and rotary-motor feedback are decoded in Application/bsp_can.c.
- The rotary mechanism uses an angle controller followed by a speed controller.
- The release servo uses TIM1 channel 1 compare values 2800 and 3500 in the current code. These are timer counts, not documented mechanical angles.
- The servo sequence calls transmit(buf), which updates display counters when the display state permits it.
- Distance sensing uses a blocking USART6 receive followed by atoi(). Units and packet framing are not specified by that conversion.
- The compression path uses the Emm V5 CAN command and reply structures.

Before connecting a host application, verify byte values, receive length, category acknowledgement / clearing, and whether commands may repeat. A complete host program and a tested transaction-level protocol are not included here.

