# Containers for Dotnet, VsCode & Rider

[![Build Status](https://travis-ci.org/justin-vanwinkle/dotnet-container.svg?branch=master)](https://travis-ci.org/justin-vanwinkle/dotnet-container)

## Quick start / TL;DR

* **To run VS Code**, grab the `code` script in the `bin` folder and execute it.
* **To run JetBrains Rider**, grab the `rider` script in the `bin` folder and execute it.
* **To use the dotnet toolchain** via command line, grab the `dotnet` script in the bin folder and execute it.

Doing any of the above will pull a prebuilt docker image and run it.  The processes for that particular item will be 100% isolated in a docker container, but it will have access to all of your files and X Forwarding (only for `code ` and `rider` will show you a GUI).

## Deeper Explanation

### Docker Run Scripts

Under `./bin` there are some simple bash scripts that build and execute
`docker run` commands for each container. You may either copy these scripts into
a location that is on your _PATH_ or you may add the `./bin` folder to your path.

### Container 1: [justinvanwinkle/dotnet](https://hub.docker.com/r/justinvanwinkle/dotnet/)

With this container and the included run script `./bin/dotnet` you can
execute the `dotnet` toolchain as if it was installed onto your local host system.

This container extends the offical [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/)
container and sets up [su-exec](https://github.com/ncopa/su-exec) to execute a 
given command as the same user as your host such that generated files will have
the correct ownership, etc.


### Container 2: [justinvanwinkle/dotnet-ide](https://hub.docker.com/r/justinvanwinkle/dotnet-ide/)
This container extends `justinvanwinkle/dotnet` and only serves as the base image for others.  It installs a bunch of X server stuff, Mono, NodeJs, TypeScript, etc.

### Container 3: [justinvanwinkle/dotnet-rider](https://hub.docker.com/r/justinvanwinkle/dotnet-rider/)

Run this with the included run script: `./bin/rider`.

This container extends `justinvanwinkle/dotnet-ide` and installs
[JetBrain's Rider IDE](https://www.jetbrains.com/rider/).


### Container 4: [justinvanwinkle/dotnet-vscode](https://hub.docker.com/r/justinvanwinkle/dotnet-vscode/)

Run this with the included run script: `./bin/code`.

This container extends `justinvanwinkle/dotnet-ide` and adds
[Microsoft's Visual Studio Code Editor](https://code.visualstudio.com/).


## Know Issues:

- Your working directory must be with-in your host users home directory. Attempting run any of the containers outside of this will result in failure.
