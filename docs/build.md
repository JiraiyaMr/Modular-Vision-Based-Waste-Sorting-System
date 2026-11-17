# Build and Reproduction

## Recorded toolchain

- Project: MDK-ARM/Dustbin.uvprojx
- Target: Dustbin
- Device: STM32F407IG
- Compiler: ARMCC 5.06 update 5, build 528
- Device pack: Keil.STM32F4xx_DFP.1.0.8
- Board configuration: Dustbin.ioc

The 71 local source references in the Keil project were checked against the repository tree at baseline commit 2b89ec5ca9b44ae4689aa969d04e9edf40cc49a9 and all resolve. This is a path check, not a fresh build.

## Procedure

1. Clone the repository and open the original Keil project.
2. Install/select the recorded compiler and STM32F4 device support; retain the original version information if testing a newer pack.
3. Build target Dustbin. Preserve compiler warnings and the build log.
4. Match the actual board, motor IDs, servo travel, sensor format, and actuator configuration.
5. Validate each subsystem before an integrated run. The current startup creates the compression task immediately.
6. Record the tested Git commit, toolchain, hardware configuration, and observed behavior.

MDK-ARM/Emm_V5.c and MDK-ARM/compress.c are source files referenced by the project. Do not delete the entire MDK-ARM directory as though it contained only generated output. Application/compress.c is another copy; changes must be applied to the version actually referenced by the project.

## Historical artifacts

The initial upload includes object files, images, maps, dependency files, build logs, and per-user µVision settings. These are historical artifacts, not evidence of a new build. The added .gitignore prevents new untracked build products from being added; it does not remove already tracked files.

Original source encodings and copyright notices are retained. Encoding conversion and firmware changes should be reviewed in a separate commit.

