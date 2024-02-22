## Examples of Assembly programming for APPS

These examples are part of study material for the basic assembly programming in the APPS subject.

To build examples use command `make` in all directories.

This fork contains modified Makefiles for use with Docker on ARM architectures like Apple Silicon. [This Docker image was used.](https://github.com/DanielKrasny/apps-asm-docker)

## How-to

1. Download and install [Docker Desktop](https://www.docker.com/products/docker-desktop/). (Docker-compatible runtimes can be used too.)
2. Download source codes.
3. Create copy of empty-project-* or try selected example.
4. If you are using macOS, make sure that terminal is not running with Rosetta.
5. Edit source codes and build them by command `make`. (Use of `sudo` might be required in specific cases.) To execute output binary, use `make run`.
6. Also it is possible to import into Eclipse-C++. Import your code as C/C++ > Existing Code as Makefile project, e.g. see
    [video](https://www.youtube.com/watch?v=E36QpJdEghg&t=2m40s), time 2:40. And many more turorials
