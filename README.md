# opu-sim

Simulator for [OPU: An FPGA-based Overlay Processor for Convolutional Neural Networks](http://eda.ee.ucla.edu/pub/J93.pdf). 
Descriptions about data structures and fucntions can be found in the [doc](https://github.com/OPU-Lab/opu-sim/blob/master/README_Summary.md).

## CMake Build
```
mkdir build
cd build
cmake ..
make
```

## Docker Build
install docker
```
sh docker_install.sh
```
build
```
sudo docker build -f Dockerfile --tag opu-sim:1.0 .
```
launch
```
sudo docker run --rm --pid=host\
                     --mount src="$(pwd)",target=/ws,type=bind\
                     -w /ws\
                     -e "CI_BUILD_HOME=/ws"\
                     -e "CI_BUILD_USER=$(id -u -n)"\
                     -e "CI_BUILD_UID=$(id -u)"\
                     -e "CI_BUILD_GROUP=$(id -g -n)"\
                     -e "CI_BUILD_GID=$(id -g)"\
                     -h fsim\
                     --name fsim\
                     -it --net=host\
                     opu-sim:1.0\
                     /bin/bash
```
detach (can attach later) : ``ctrl+p`` followed by ``ctrl+q``

exit (cannot attach later): ``exit``
