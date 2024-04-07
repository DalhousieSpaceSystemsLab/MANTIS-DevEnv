# MANTIS DevEnv
Common and cross-platform development environment for the MANTIS CubeSat.

## Tech Stack
The DevEnv is made possible by [Nix](https://nix.dev/). 

Nix ensures that the terminal session used for development (which it dubs 'ad-hoc shell') contains all the necessary prerequisites as defined in `shell.nix`.

This is preferable (in my estimation) to the use of Docker Container environments as it is much less bulky and makes the most use of the existing resources on the host system. It also prevents many of the headaches associated with bridging the inner isolated environments of Docker containers to that of the native machine (e.g.: USB ports, serial connections, network access, etc).

### Included packages
By default, the following Nix packages are auto-installed when entering the DevEnv:

- gcc-arm-embedded
- stlink
- cmake
- openocd
- vim

## Getting Started
To get started, clone the repo on a Windows (WSL), MacOS or Linux system:

```
$ git clone git@github.com:DalhousieSpaceSystemsLab/MANTIS-DevEnv.git
```

### Running the `bootstrap.sh` script
Run the `boostrap.sh` script:

```
$ ./bootstrap.sh
```

This will primarily install [Nix](https://nix.dev/) on your machine, a prerequisite for the MANTIS DevEnv.

## Entering the DevEnv
Once Nix is installed, the MANTIS DevEnv must be entered by running 

```
$ ./devenv.sh
```

in the root of the repo.

The same can be done manually by running `nix-shell -v` in the root of the repo. 

_This step is mandatory to ensure all required build dependencies and tooling are available_.

_NOTE_: If you have not restarted your shell after installing Nix, this may explain why this step is not working.

## Building, Flashing and Debugging
Once entered the DevEnv, you'll be in an ad-hoc shell environment with all of the build dependencies needed for the project to build.

```
[nix-shell:~/MANTIS-STM32_Base_Project]$ echo "hello"
```

You can inspect the [shell.nix](/shell.nix) file to see what dependencies are fetched.
