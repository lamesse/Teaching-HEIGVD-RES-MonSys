# Answers, Phase 1

```
# -- INSERT YOUR NAMES HERE -----
Arnaud Desclouds
Antoine Messerli

We certify that we have done all the lab tasks and we have a running environment on our 
machine to prove it. We are ready to demonstrate it at any time and to explain the process
we have followed.
# -------------------------------
```
Docker ps to know the running container

```
# -- YOUR ANSWER TO QUESTION 1 --

# -------------------------------
```
$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Box 'phusion-open-ubuntu-14.04-amd64' could not be found. Attemptin
g to find and install...
    default: Box Provider: virtualbox
    default: Box Version: >= 0
==> default: Adding box 'phusion-open-ubuntu-14.04-amd64' (v0) for provider: vir
tualbox
    default: Downloading: https://oss-binaries.phusionpassenger.com/vagrant/boxe
s/latest/ubuntu-14.04-amd64-vbox.box
    default: Progress: 100% (Rate: 4570k/s, Estimated time remaining: --:--:--)
==> default: Successfully added box 'phusion-open-ubuntu-14.04-amd64' (v0) for '
virtualbox'!
==> default: Importing base box 'phusion-open-ubuntu-14.04-amd64'...
==> default: Matching MAC address for NAT networking...
==> default: Setting the name of the VM: monsys-web-infra_default_1399531250534_
37320
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
    default: Adapter 2: hostonly
==> default: Forwarding ports...
    default: 9090 => 8080 (adapter 1)
    default: 22 => 2222 (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Connection timeout. Retrying...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
==> default: Configuring and enabling network interfaces...
==> default: Mounting shared folders...
    default: /vagrant => D:/Google Drive/HEIG-VD/RES/Lab8-9_monSys/Teaching-HEIG
VD-RES-MonSys/monsys-web-infra
==> default: Running provisioner: shell...
    default: Running: inline script
==> default: stdin: is not a tty
==> default: Cleaning up Docker containers...
==> default: /tmp/vagrant-shell: line 2: docker: command not found
==> default: /tmp/vagrant-shell: line 3: docker: command not found
==> default: /tmp/vagrant-shell: line 4: docker: command not found
==> default: /tmp/vagrant-shell: line 5: docker: command not found
==> default: /tmp/vagrant-shell: line 6: docker: command not found
==> default: /tmp/vagrant-shell: line 7: docker: command not found
==> default: /tmp/vagrant-shell: line 8: docker: command not found
==> default: /tmp/vagrant-shell: line 9: docker: command not found
==> default: Running provisioner: docker...
    default: Installing Docker (latest) onto machine...
    default: Configuring Docker to autostart containers...
==> default: Building Docker images...
==> default: -- Path: /vagrant/docker/rp-nginx
The following SSH command responded with a non-zero exit status.
Vagrant assumes that this means the command failed!

docker build -t heig/rp-nginx /vagrant/docker/rp-nginx

Stdout from the command:

Step 0 : FROM dockerfile/ubuntu
Pulling repository dockerfile/ubuntu


Stderr from the command:

stdin: is not a tty
Uploading context 16.38 kB
Uploading context
2014/05/08 06:43:36 Could not reach any registry endpoint

Vagrant provision

$ vagrant provision
==> default: Running provisioner: shell...
    default: Running: inline script
==> default: stdin: is not a tty
==> default: Cleaning up Docker containers...
==> default: Error: No such container: rp-node
==> default: 2014/05/08 07:17:28 Error: failed to stop one or more containers
==> default: Error: No such container: web-node-1
==> default: 2014/05/08 07:17:28 Error: failed to stop one or more containers
==> default: Error: No such container: web-node-2
==> default: 2014/05/08 07:17:28 Error: failed to stop one or more containers
==> default: Error: No such container: app-node
==> default: 2014/05/08 07:17:28 Error: failed to stop one or more containers
==> default: Error: No such container: rp-node
==> default: 2014/05/08 07:17:28 Error: failed to remove one or more containers
==> default: Error: No such container: web-node-1
==> default: 2014/05/08 07:17:29 Error: failed to remove one or more containers
==> default: Error: No such container: web-node-2
==> default: 2014/05/08 07:17:29 Error: failed to remove one or more containers
==> default: Error: No such container: app-node
==> default: 2014/05/08 07:17:29 Error: failed to remove one or more containers
==> default: Running provisioner: docker...
    default: Configuring Docker to autostart containers...
==> default: Building Docker images...
==> default: -- Path: /vagrant/docker/rp-nginx
==> default: -- Path: /vagrant/docker/web-apache
==> default: -- Path: /vagrant/docker/app-nodejs
==> default: Starting Docker containers...
==> default: -- Container: rp-node
==> default: -- Container: web-node-1
==> default: -- Container: web-node-2
==> default: -- Container: app-node
```

# -- YOUR ANSWER TO QUESTION 2 --

# -------------------------------
```
Linux ubuntu-14 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x8
6_64 x86_64 x86_64 GNU/Linux
```
# -- YOUR ANSWER TO QUESTION 3 --

# -------------------------------
```
vagrant@ubuntu-14:~$ docker images
```

```
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
```

```
heig/app-nodejs     latest              ac1d4953cb0e        7 minutes ago       398.9 MB
```

```
heig/web-apache     latest              17dfd976322a        10 minutes ago      411.9 MB
```

```
heig/rp-nginx       latest              1f1a411d474b        15 minutes ago      637.9 MB
```

```
dockerfile/ubuntu   latest              cbc81be8f75e        12 days ago         378.6 MB
```
# -- YOUR ANSWER TO QUESTION 4 --

# -------------------------------
```
vagrant@ubuntu-14:~$ docker ps
```

```
CONTAINER ID        IMAGE                    COMMAND                CREATED             STATUS             PORTS                  NAMES
```

```
5032c516d6c1        heig/app-nodejs:latest   node /opt/server.js    8 minutes ago       Up 8 minutes        0.0.0.0:7070->80/tcp   app-node
```

```
f08a079287ad        heig/web-apache:latest   /usr/sbin/apache2ctl   8 minutes ago       Up 8 minutes        0.0.0.0:8082->80/tcp   web-node-2
```

```
e38eea89d56d        heig/web-apache:latest   /usr/sbin/apache2ctl   8 minutes ago       Up 8 minutes        0.0.0.0:8081->80/tcp   web-node-1
```
# -- YOUR ANSWER TO QUESTION 5 --

# -------------------------------
```
web-node-2 : ip : 0.0.0.0
web-node-1 : ip : 0.0.0.0
rp-node : ip : 0.0.0.0
app-node : ip : 0.0.0.0
```
# -- YOUR ANSWER TO QUESTION 6 --

Host (your laptop):
- IP address: H.H.H.H

Virtual Machine run by Virtual Box
- IP address: B.B.B.B
- PAT: packets arriving on H.H.H.H:PH are forwarded to B.B.B.B:PB

Docker Bridge
- IP address: DB.DB.DB.DB
- PAT: packets arriving on DB.DB.DB.DB:PB1 are forwarded to C1.C1.C1.C1:PC1
- PAT: packets arriving on DB.DB.DB.DB:PB2 are forwarded to C2.C2.C2.C2:PC2
- PAT: packets arriving on DB.DB.DB.DB:PB3 are forwarded to C3.C3.C3.C3:PC3
- PAT: packets arriving on DB.DB.DB.DB:PB4 are forwarded to C4.C4.C4.C4:PC4

Docker Container 1
- IP address: C1.C1.C1.C1

Docker Container 2
- IP address: C2.C2.C2.C2

Docker Container 3
- IP address: C3.C3.C3.C3

Docker Container 4
- IP address: C4.C4.C4.C4

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 7 --

Which command did you type on the terminal to establish the connection?

What HTTP request did you type and send?

What HTTP response did you get?
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 8 --

Which command did you type on the terminal to establish the connection?

What HTTP request did you type and send?

What HTTP response did you get?
# -------------------------------
```




