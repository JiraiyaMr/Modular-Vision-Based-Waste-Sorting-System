# Demonstration and Contribution Evidence

This repository is the embedded-controller part of the waste-sorting project. A strong demonstration can connect an incoming category command, the transport / sorting action, and the resulting physical placement.

## Sorting workflow

![Multi-item waste-sorting workflow](../figures/sorting_workflow_en.svg)

English rendering of the project workflow: item transport and detection, image-based classification, category transmission, and the discharge / bin-full detection branches.

## Evidence to attach

| Item | Useful content |
| --- | --- |
| Prototype photograph | Annotated conveyor, sorter, release, sensor and controller locations |
| Short video | Category input, physical sorting sequence, and display response |
| Tested configuration | Board revision, motor IDs, calibration, servo limits, sensor units and firmware commit |
| Measurement record | Trial conditions, sample count, successes / failures and measured cycle-time definition |
| Personal contribution | Modules implemented, existing libraries integrated, tuning / debugging work and tests personally performed |

No photograph, video, test dataset, classification benchmark, or individual authorship breakdown has been added in this documentation update. Add those when the underlying evidence is available; source inspection alone does not supply measured accuracy or timing.

The embedded design and integration work should be distinguished from the host-side recognition model and from vendor / shared communication libraries. The developer's dated main.c notes provide a useful chronology, while a personal contribution statement should name the actual modules and work performed.


## Video recordings

| Demonstration | Playback | Repository file |
| --- | --- | --- |
| System operation | [Watch video](https://jiraiyamr.github.io/assets/videos/waste-sorting/operation.mp4) | [MP4](../media/videos/operation.mp4) |
