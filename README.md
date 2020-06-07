# balena-cloud
 Shell scripts package of containers native interface from Balena Cloud

## Usage
deploy.sh: place it in the root folder of the project.
```Shell
#!/usr/bin/env bash
### Paste in here latest File Revisions
REV=https://raw.githubusercontent.com/b23prodtm/vagrant-shell-scripts/b23prodtm-patch/vendor/cni/balena_deploy.sh
#REV=https://raw.githubusercontent.com/b23prodtm/vagrant-shell-scripts/87e48481c955e213de3d08453dd4dd56d1104bec/vendor/cni/balena_deploy.sh
sudo curl -SL -o /usr/local/bin/balena_deploy $REV
sudo chmod 0755 /usr/local/bin/balena_deploy
source balena_deploy ${BASH_SOURCE[0]} "$@"
```
Copy test/build/ folder to the root folder of your project
Make changes to the Dockerfile, common.env and <arch>.env files
## Environment Variables
There are some data information to complete and describe the project.
It follows that:
````common.env
BALENA_PROJECTS=(MY/PATH MY/RELATIVE/PATH)
BALENA_PROJECTS_FLAGS=(BALENA_MACHINE_NAME MY_VARIABLE)
```
Architectures: ARM is armhf and aarch64, INTEL/AMD is x86_64
```x86_64.env
DKR_ARCH=x86_64
BALENA_MACHINE_NAME=intel-nuc
IMG_TAG=latest
PRIMARY_HUB=docker-hub-balenalib-repo\\/container-servìce-image
```
In a BASH terminal, type for instance:
```Console
./deploy.sh x86_64 --nobuild --exit
./deploy.sh armhf --balena
```
## Test
Run unit tests on local host or CI

    cd test
    # DEBUG=1
    ./build-tests.sh
