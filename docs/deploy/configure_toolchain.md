# Configure the toolchain
The toolchain can be setup either from a docker container or locally, the docker container being the prefered way as it contains a fully tested environment. See below for instructions regarding the installation.

## From a local machine
### Clone the repo
It's important to clone the repo with it's submodule. You can do this with one of these two options.

> Note : # pickup the latest stable release from [https://github.com/Azure/az-hop/releases](https://github.com/Azure/az-hop/releases) and replace `<version>`

- Option 1
```bash
git clone --recursive https://github.com/Azure/az-hop.git -b <version>
```
 
- Option 2
```bash
git clone https://github.com/Azure/az-hop.git -b <version>
cd az-hop
git submodule init
git submodule update
```

### HPC Rover - Setup the toolchain from a container

The `HPC Rover` is a docker container acting as a sandbox toolchain development environment to avoid impacting the local machine configuration. It is the same container if you are using Windows, Linux or macOS, you only need Visual Studio Code.

<img src="https://code.visualstudio.com/assets/docs/remote/containers/architecture-containers.png" width="75%">

You can learn more about the Visual Studio Code Remote on this [link](https://code.visualstudio.com/docs/remote/remote-overview).

To start the container in VS Code, simply open the cloned repository directory (from the **File** menu or by using `code .` from the cloned directory in a separate WSL instance) and click on **Reopen in Container** in the pop-up notification in the bottom right corner.

#### Pre-requisites

The Visual Studio Code system requirements describe the steps to follow to get your development environment ready -> [link](https://code.visualstudio.com/docs/remote/containers#_system-requirements)

* **Windows**: Docker Desktop 2.0+ on Windows 10 Pro/Enterprise with Linux Container mode
* **macOS**: Docker Desktop 2.0+
* **Linux**: Docker CE/EE 18.06+ and Docker Compose 1.24+

The `HPC Rover` is a Ubuntu 20.04 base image and is hosted on the Docker Hub [Link](https://hub.docker.com/r/xpillons/hpcrover/tags?page=1&ordering=last_updated)

Install
* Visual Studio Code version 1.41+ - [link](https://code.visualstudio.com/Download)
* Install Visual Studio Code Extension - Remote Development - [link](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)

### Setup on Ubuntu (e.g. WSL2)
This is not the recommended way, but still remain a doable way.
For Terraform to work properly on  WSL2, on the C drive, make sure to have the metadata mount option enabled.
Run the `install.sh` from the _toolset/scripts_ directory in Ubuntu 20.04.

```bash
./toolset/scripts/install.sh
```

## From a deployer VM
`az-hop` can be deployed directly from an Ubuntu Azure VM used preferably behind a Bastion, in that case do the following :
- Create a Bastion
- Create a `deployer` VM running Ubuntu without a public IP
- Connect to the `deployer` VM from Bastion
- Clone the repo as explained above
- Install the toolset by running `sudo ./az-hop/toolset/scripts/install.sh`


