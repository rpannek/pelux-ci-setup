# Jenkins

Here you can find the files needed to set up a Jenkins docker container. For now we only need the systemd service file which will download the right image from docker hub install and run it.

It will save the configuration in a docker volume called `jenkins_home`.

## Usage

    cp docker.jenkins.service /lib/systemd/system/
    systemctl enable docker.jenkins.service
    systemctl start docker.jenkins.service
    

