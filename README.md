# ESP-IDF Dev Environment
This repository provides a Docker-based development environment for ESP32 projects using ESP-IDF.


## Purpose
Containerize the ESP-IDF build toolchain while keeping device flashing and debugging on the host machine. This approach provides:

- Consistent build environment across different development machines.
- Isolated dependencies without polluting the host system.

## Development Strategy

### Build in Container
- Compile ESP32 projects inside the DevContainer using Espressif's Docker image with all ESP-IDF tools pre-installed.
- Generated build artifacts are accessible via mounted volumes.

### Flash on Host
- Use `esptool.py` installed locally to flash the compiled binaries to the physical ESP32 device.
- Direct USB/serial access avoids container complexities and limitations (e.g. cannot pass usbserial from macOS into Docker).

### Debug on Host
- Run live debugging tools (OpenOCD, GDB, serial monitors) directly on the host.
- Maintains reliable connection to hardware without container networking overhead.

This hybrid approach leverages containerization benefits for the build process while maintaining straightforward hardware interaction on the host.
