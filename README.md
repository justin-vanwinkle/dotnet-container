# Containers for Dotnet, VsCode & Rider
[![Build Status](https://travis-ci.org/justin-vanwinkle/dotnet-container.svg?branch=master)](https://travis-ci.org/justin-vanwinkle/dotnet-container)
 
__THESE CONTAINERS ARE NOT FOR PRODUCTION USE BUT FOR LOCAL DEVELOPMENT__

## Docker Run Scripts
Under `./bin` there are some simple bash scripts that build and execute
`docker run` commands for each container. You may either copy these scripts into
a location that is on your _PATH_ or you may add the `./bin` folder to your path.

## Container 1: justinvanwinkle/dotnet
This container extends the offical [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/)
container and sets up [su-exec](https://github.com/ncopa/su-exec) to execute a 
given command as the same user as your host such that generated files will have
the correct ownership, etc.

So with this container and the included run script `./bin/dotnet` you can
execute the `dotnet` toolchain as if it was installed onto your local host system.

## Container 2: justinvanwinkle/dotnet-ide
This container does not provide any addtional functionality by it's self,
it only serves as the base image for both the vscode and rider images.
It installs a bunch of X server stuff, Mono, NodeJs, TypeScript, etc.

## Container 3: justinvanwinkle/dotnet-rider
This container extends `justinvanwinkle/dotnet-ide` and installs
[JetBrain's Rider IDE](https://www.jetbrains.com/rider/).

You can easily run this with the included run script: `./bin/rider`.

## Container 4: justinvanwinkle/dotnet-vscode
This container extends `justinvanwinkle/dotnet-ide` and installs
[Microsoft's Visual Studio Code Editor](https://code.visualstudio.com/).

You can easily run this with the included run script: `./bin/code`.

## Know Issues:

- The way I have setup the run scripts for the containers, your working
  directory must be with-in your host users home directory. Attempting run
  any of the containers outside of this will result in failure.
