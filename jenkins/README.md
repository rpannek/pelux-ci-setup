# Jenkins

Here you can find the files needed to set up a Jenkins docker container. For now we only need the systemd service file which will download the right image from docker hub install and run it.

It will save the configuration in a docker volume called `jenkins_home`.

## Usage

    apt install docker.io
    cp docker.jenkins.service /lib/systemd/system/
    systemctl enable docker.jenkins.service
    systemctl start docker.jenkins.service
    
Starting it the first time can take a couple of minutes depending on your internet connection because it then downloads the docker image ands sets everything up, so be patient.

Once it is started you need the admin password which you can find in the logs:

    journalctl -b -u docker.jenkins
    ...
    Jul 03 12:37:22 vps429458 docker[9553]: Jenkins initial setup is required. An admin user has been created and a password generated.
    Jul 03 12:37:22 vps429458 docker[9553]: Please use the following password to proceed to installation:
    Jul 03 12:37:22 vps429458 docker[9553]: 932c528c68d14e24aab036f2021e2dee
    Jul 03 12:37:22 vps429458 docker[9553]: This may also be found at: /var/jenkins_home/secrets/initialAdminPassword

Then you can open this jenkins instance in your browser and put this password there so you can set everything up:

    http://localhost:8080/jenkins/
    
After that you can also set up a nginx instance as a proxy so you don't need the port number in the URL, but you don't need to do that on your development machine.

## Plugins

Normally we use the proposed plugins during installation and then add the following:

- Copy Artifact Plugin
