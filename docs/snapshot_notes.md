# Archived Configuration and Engineering Follow-Up

These observations describe the uploaded source, not measured behavior of every historical prototype. Firmware has not been changed by the documentation update.

| Source | Observation | Follow-up before reproducing the demonstration |
| --- | --- | --- |
| Application/sort_motor.c | sort_ctrl() uses switch(1), while category cases are ASCII '1' to '4'. The default / fixed-position path is therefore selected. | Identify the intended demonstration revision and restore category selection only after checking calibration. |
| Application/type.c | type_judge() assigns the current value to both history fields before comparing them. | Revise the update order if temporal confirmation is intended. |
| Core/Src/freertos.c | Laser and PC task configuration reuses Pc_Task_Handler and repeats the PC stack-size definition. | Give each task its own handle and configuration names. |
| Core/Src/main.c; Core/Src/freertos.c | USB device initialization occurs in two startup locations. | Establish one intended initialization point. |
| Application/compress.c | Compression repeatedly commands forward/backward motion and waits indefinitely for replies. | Define triggering, timeout, fault handling, and coordination with sorting. |
| Application/laser_distance.c | A fixed-length blocking receive is followed by string scanning and atoi(). | Check packet boundaries, termination, units, and bounds on the actual sensor stream. |
| Application/usart_screen.c | LCD_task exists but is not started by the archived RTOS configuration. | Check the display initialization and page-state path used in the working prototype. |

The category-dependent mechanism, host handshake, and mechanical calibration should be validated together when a working revision is identified. Historical integration milestones are retained separately in the development timeline.

