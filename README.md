# rancher-introduction-lab

## Prerequisites

### Windows

If running windows, it is required for this lab to run rancher on docker in a linux-based VM.
https://www.virtualbox.org/wiki/Downloads
https://www.vagrantup.com/downloads.html

Use the Vagrant file embedded in this github-project and start a lightweight Ubuntu-based vm with Vagrant.

Save the Vagrantfile locally and from the same folder type:
```
vagrant up
```
If needed, make sure to port forward from guest to host by editing the Vagrantfile i.e:
```
config.vm.network "forwarded_port", guest: 8080, host: 8080
```

When booted up in the vm, ssh to the vagrant vm:
```
vagrant ssh
```

install docker by running the script below in the terminal:
```
curl https://releases.rancher.com/install-docker/1.12.sh | sh
```


### MacOS or Linux

Rancher is compatible with both MacOs and Linux so it works just fine to run the lab natively on your laptop.
You can of course use virtualbox and Vagrant if you prefer. If so, see the instructions for Windows above

## Install Rancher Agent

Installing the Rancher agent is rather straigh forward.

Simply start a container with docker run:
```
sudo docker run -d --restart=unless-stopped -p 8080:8080 rancher/server
```

After the container is started and rancher is installed, try access rancher web console in the browser.

## Add a Rancher host
For simplicity we will add a new host on the same host as the agent. Normally a host is located on a different server.

Click Infrasrtucture -> Hosts -> Add host
Follow the instructions.

## Add a new stack

Browse the Rancher catalog and add a new stack to your rancher host.

## Bonus task

Add a custom stack by referencing a docker-compose file from previous excercises and scale it by either specify it
with rancher-compose or by changing the scale when running
