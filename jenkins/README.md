# Jenkins

Here you can find the files needed to set up a Jenkins docker container. For now we only need the systemd service file which will download the right image from docker hub install and run it.

It will save the configuration in a docker volume called `jenkins_home`.

## Usage

    apt install docker.io
    cp docker.jenkins.service /lib/systemd/system/
    systemctl enable docker.jenkins.service
    systemctl start docker.jenkins.service
    
Starting it the first time can take a couple of minutes depending on your internet connection because it then downloads the docker image ands sets everything up, so be patient.
