# Docker container images with "headless" VNC session

The repository contains a collection of Docker images with headless VNC environments.

Each docker image is installed with the following components:

* Desktop environment [**Xfce4**](http://www.xfce.org) or [**IceWM**](http://www.icewm.org/)
* VNC-Server (default VNC port `5901`)
* [**noVNC**](https://github.com/kanaka/noVNC) - HTML5 VNC client (default http port `6901`)
* Browsers:
  * Mozilla Firefox
  * Chromium

## Current provided OS & UI sessions:
* `consol/centos-xfce-vnc`: __Centos7 with `Xfce4` UI session__ 

  [![](https://images.microbadger.com/badges/version/consol/centos-xfce-vnc.svg)](https://hub.docker.com/r/consol/centos-xfce-vnc/) [![](https://images.microbadger.com/badges/image/consol/centos-xfce-vnc.svg)](http://microbadger.com/images/consol/centos-xfce-vnc)

* `consol/ubuntu-xfce-vnc`: __Ubuntu with `Xfce4` UI session__

  [![](https://images.microbadger.com/badges/version/consol/ubuntu-xfce-vnc.svg)](https://hub.docker.com/r/consol/ubuntu-xfce-vnc/) [![](https://images.microbadger.com/badges/image/consol/ubuntu-xfce-vnc.svg)](http://microbadger.com/images/consol/ubuntu-xfce-vnc)

* `consol/centos-icewm-vnc`: __Centos7 with `IceWM` UI session__ 

  [![](https://images.microbadger.com/badges/version/consol/centos-icewm-vnc.svg)](https://hub.docker.com/r/consol/centos-icewm-vnc/) [![](https://images.microbadger.com/badges/image/consol/centos-icewm-vnc.svg)](http://microbadger.com/images/consol/centos-icewm-vnc)

* `consol/ubuntu-icewm-vnc`: __Ubuntu with `IceWM` UI session__

  [![](https://images.microbadger.com/badges/version/consol/ubuntu-icewm-vnc.svg)](https://hub.docker.com/r/consol/ubuntu-icewm-vnc/) [![](https://images.microbadger.com/badges/image/consol/ubuntu-icewm-vnc.svg)](http://microbadger.com/images/consol/ubuntu-icewm-vnc)


## Latest Changes
See the [**changelog.md**](./changelog.md).

## Usage
The usage is for all provide images **similar**, for instance see following the usage of the `consol/centos-xfce-vnc` image:

Run command with mapping to local port `5901` (vnc protocol) and `6901` (vnc web access):

    docker run -d -p 5901:5901 -p 6901:6901 consol/centos-xfce-vnc
  
Change the default user and group within a container to your own with adding `--user $(id -u):$(id -g)`:

    docker run -d -p 5901:5901 -p 6901:6901 --user $(id -u):$(id -g) consol/centos-xfce-vnc

If you wan't to get into the container use  interactive mode `-it` and `bash`     

    docker run -d -p 5901:5901 -p 6901:6901 consol/centos-xfce-vnc

Build a image from scratch:

    docker build -t consol/centos-xfce-vnc centos-xfce-vnc

=> connect via __VNC viewer `localhost:5901`__, default password: `vncpassword`

=> connect via __noVNC HTML5 client__: [http://localhost:6901/?password=vncpassword]()


## Hints
### Override the VNC password
Simple override the value of the environment variable `VNC_PW`. For example in
the docker run command:

    docker run -it -p 5901:5901 -p 6901:6901 -e "VNC_PW=my-new-password" consol/centos-xfce-vnc
    
### Override the VNC resolution
Simple override the value of the environment variable `VNC_RESOLUTION`. For example in
the docker run command:

    docker run -it -p 5901:5901 -p 6901:6901 -e VNC_RESOLUTION=800x600 consol/centos-xfce-vnc


## Contact
For questions, professional support or maybe some hints, feel free to contact us via **[testautomatisierung@consol.de](mailto:testautomatisierung@consol.de)** or open an [issue](https://github.com/ConSol/docker-headless-vnc-container/issues/new).

The guys behind:

**ConSol Software GmbH** <br/>
*Franziskanerstr. 38, D-81669 München* <br/>
*Tel. +49-89-45841-100, Fax +49-89-45841-111*<br/>
*Homepage: http://www.consol.de E-Mail: [info@consol.de](info@consol.de)*
