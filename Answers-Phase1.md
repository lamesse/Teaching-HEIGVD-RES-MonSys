# Answers, Phase 1

# -- INSERT YOUR NAMES HERE -----
Arnaud Desclouds
Antoine Messerli

We certify that we have done all the lab tasks and we have a running environment on our 
machine to prove it. We are ready to demonstrate it at any time and to explain the process
we have followed.
# -------------------------------

# -- YOUR ANSWER TO QUESTION 1 --

# -------------------------------
	$ vagrant up
	Bringing machine 'default' up with 'virtualbox' provider...
	==> default: Box 'phusion-open-ubuntu-14.04-amd64' could not be found. Attempting to find and install...
    default: Box Provider: virtualbox
    default: Box Version: >= 0
	==> default: Adding box 'phusion-open-ubuntu-14.04-amd64' (v0) for provider: virtualbox
    default: Downloading: https://oss-binaries.phusionpassenger.com/vagrant/boxes
	/latest/ubuntu-14.04-amd64-vbox.box
    default: Progress: 100% (Rate: 4570k/s, Estimated time remaining: --:--:--)
	==> default: Successfully added box 'phusion-open-ubuntu-14.04-amd64' (v0) for '
	virtualbox'!
	==> default: Importing base box 'phusion-open-ubuntu-14.04-amd64'...
	==> default: Matching MAC address for NAT networking...
	==> default: Setting the name of the VM: monsys-web-infra_default_1399531250534_37320
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

# -- YOUR ANSWER TO QUESTION 2 --

# -------------------------------

	Linux ubuntu-14 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x8
	6_64 x86_64 x86_64 GNU/Linux

# -- YOUR ANSWER TO QUESTION 3 --

# -------------------------------

	vagrant@ubuntu-14:~$ docker images
	REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
	heig/app-nodejs     latest              9b73730328a0        10 hours ago        609.4 MB
	heig/web-apache     latest              fc111b8fcac7        10 hours ago        623.3 MB
	heig/rp-nginx       latest              0d9553a2918a        10 hours ago        957 MB
	dockerfile/ubuntu   latest              1f089cc15e82        3 days ago          584.5 MB


# -- YOUR ANSWER TO QUESTION 4 --

# -------------------------------

	vagrant@ubuntu-14:~$ docker ps
	CONTAINER ID        IMAGE                    COMMAND                CREATED             STATUS              PORTS
	           NAMES
	e1a19d00a61c        heig/app-nodejs:latest   node /opt/server.js    10 hours ago        Up 10 hours         0.0.0.0:7070
	->80/tcp   app-node
	e8b1f01613e2        heig/web-apache:latest   /usr/sbin/apache2ctl   10 hours ago        Up 10 hours         0.0.0.0:8082
	->80/tcp   web-node-2
	129bcbc7f4b5        heig/web-apache:latest   /usr/sbin/apache2ctl   10 hours ago        Up 10 hours         0.0.0.0:8081
	->80/tcp   web-node-1
	d9ce100be0cd        heig/rp-nginx:latest     /opt/init.sh           10 hours ago        Up 10 hours         0.0.0.0:9090
	->80/tcp   rp-node


# -- YOUR ANSWER TO QUESTION 5 --

# -------------------------------

	web-node-2 : ip : 172.17.0.4
	web-node-1 : ip : 172.17.0.3
	rp-node : ip : 172.17.0.2
	app-node : ip : 172.17.0.5

# -- YOUR ANSWER TO QUESTION 6 --

Host (your laptop):
- IP address: 10.192.85.21

Virtual Machine run by Virtual Box
- IP address: 192.168.33.20
- PAT: packets arriving on 192.168.33.20:9090 are forwarded to 172.17.41.1:80

Docker Bridge
- IP address: 172.17.42.1

- PAT: packets arriving on 172.17.42.1:8081 are forwarded to 172.17.0.3:80

- PAT: packets arriving on 172.17.42.1:8082 are forwarded to 172.17.0.4:80

- PAT: packets arriving on 172.17.42.1:7070 are forwarded to 172.17.0.5:80

- PAT: packets arriving on 172.17.42.1:9090 are forwarded to 172.17.0.2:80

Docker Container 1 web-node-2

- IP address: 172.17.0.4

Docker Container 2 web-node-1

- IP address: 172.17.0.3

Docker Container 3 rp-node

- IP address: 172.17.0.2

Docker Container 4 app-node

- IP address: 172.17.0.5

# -------------------------------

# -- YOUR ANSWER TO QUESTION 7 --

Which command did you type on the terminal to establish the connection?


	telnet www.monsys.com 9090


What HTTP request did you type and send?

	GET / HTTP/1.1
	HOST:www.monsys.com



What HTTP response did you get?
# -------------------------------

	HTTP/1.1 200 OK
	Server: nginx/1.6.0
	Date: Thu, 15 May 2014 07:44:29 GMT
	Content-Type: text/html
	Content-Length: 1584
	Connection: keep-alive
	X-Powered-By: PHP/5.5.9-1ubuntu4
	Vary: Accept-Encoding
	<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
	        "http://www.w3.org/TR/html4/loose.dtd">
	<html>
	        <head>
	                <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
	                <link href='http://fonts.googleapis.com/css?family=Terminal+Dosi
	s' rel='stylesheet' type='text/css'>
	                <link href='css/main.css' rel='stylesheet' type='text/css'>
	                <script type="text/javascript" src="script/jquery-1.6.4.js"></script>
	                <title>Welcome To MonSys Front-End</title>
	                <script language="JavaScript">
	                        $(document).ready(function () {
	                                refreshNodes();
	                        });
	                        function refreshNodes() {
	                            $.getJSON('/ajax/resources/nodes',
	                            function(data) {
	                                var items = [];
	                                $.each(data,
	                                function(key, val) {
	                                    items.push('<li>' + val.name + ", " + val.de
	scription + ", load: " + val.currentLoadLevel + ' %</li>');
	                                });
	                                $('#monitor').html("<ul>" + items.join('') + "</ul>");
	                            });
	                                var t=setTimeout("refreshNodes()", 1000);
	                        }
	        </script>
	        </head>
	        <body>
	                <h1>Welcome to MonSys</h1>
	                <h2>You are connected to the front-end system, implemented in PH
	P</h2>
	                <b>Note</b>: this page is sending HTTP GET requests to <verbatim
	>/ajax/resources/nodes</verbatim> in order to retrieve JSON representations of t
	he resources managed by the back-end.
	                <p/>
	                <div id="monitor">
	                        You should monitoring data coming from the back-end here.
	                </div>
	                <br/>
	                Brought to you by the University of Applied Sciences of Western
	Switzerland
	        </body>
	</html>

# -- YOUR ANSWER TO QUESTION 8 --

Which command did you type on the terminal to establish the connection?

	telnet www.monsys.com 7070

What HTTP request did you type and send?


	GET / HTTP/1.1

What HTTP response did you get?

	[{"name":"P-001","description":"Epson Printer","currentLoadLevel":22.49356652610004},{"name":"P-002","description":"Canon Printer","currentLoadLevel":0.7786028552800417},{"name":"P-003","description":"HP Printer","currentLoadLevel":28.70554516557604}]

# -------------------------------

# -- YOUR ANSWER TO QUESTION 9 --

What procedure did you follow to validate the configuration of 
your new web nodes? 

On a fait un telnet depuis la machine virtuelle vers les 3 dockers en utilisant les deux hosts configurés (leaderboard.clashofclasses.ch et live.clashofclasses.ch. On a vérifié que l'on obtenait le bon résultat.

Provide details and evidence (command results, etc.) that your 
setup is correct.


Test sur web-clash-1 - 172.17.0.6

	telnet 172.17.0.6 80
	GET / HTTP/1.1
	HOST:live.clashofclasses.ch

	HTTP/1.1 200 OK
	Date: Sat, 24 May 2014 13:26:44 GMT
	Server: Apache/2.4.7 (Ubuntu)
	Last-Modified: Thu, 22 May 2014 19:30:10 GMT
	ETag: "80a-4fa0224231480"
	Accept-Ranges: bytes
	Content-Length: 2058
	Vary: Accept-Encoding
	Content-Type: text/html
	
	<!DOCTYPE html>
	<html lang="en">
	  <head>
	    <meta charset="utf-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1">
	    <meta name="description" content="">
	    <meta name="author" content="">
	        <link href="http://netdna.bootstrapcdn.com/font-awesome/4.0.3/css/font-awesome.css" rel="stylesheet">
	    <title>Sticky Footer Template for Bootstrap</title>
	
	    <!-- Bootstrap core CSS -->
	    <link href="./css/live-bootstrap.css" rel="stylesheet">
	
	    <!-- Custom styles for this template -->
	    <link href="./css/sticky-footer.css" rel="stylesheet">
	
	    <!-- Just for debugging purposes. Don't actually copy this line! -->
	    <!--[if lt IE 9]><script src="../../assets/js/ie8-responsive-file-warning.js"></script><![endif]-->
	
	    <!-- HTML5 shim and Respond.js IE8 support of HTML5 elements and media queries -->
	    <!--[if lt IE 9]>
	      <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
	      <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
	    <![endif]-->
	  </head>
	
	  <body>
	
	    <!-- Begin page content -->
	    <div class="container">
	      <div class="page-header">
	        <h1>Welcome To Clash of Classes!</h1>
	      </div>
	      <p class="lead">This is the Welcome Page for the <b>live</b> section of the website, which is accessible at this U
	RL <a href="http://live.clashofclasses.ch">http://live.clashofclasses.ch</a>.</p>
	      <p class="lead">You can jump to the <b>dashboard</b> section of the website <a href="http://dashboard.clashofclass
	es.ch">here</a>.</p>
	
	        <p></p>
	                <img src="success.jpg" width="300">
	        <p></p>
	
	
	    </div>
	
	
	    <div id="footer">
	      <div class="container">
	        <p class="text-muted">We <i class="fa fa-heart"></i> Application Level Protocols</p>
	      </div>
	    </div>
	
	
	    <!-- Bootstrap core JavaScript
	    ================================================== -->
	    <!-- Placed at the end of the document so the pages load faster -->
	  </body>
	</html>


	telnet 172.17.0.6 80
	GET / HTTP/1.1
	HOST:leaderboard.clashofclasses.ch

	HTTP/1.1 200 OK
	Date: Sat, 24 May 2014 13:29:12 GMT
	Server: Apache/2.4.7 (Ubuntu)
	Last-Modified: Thu, 22 May 2014 19:30:10 GMT
	ETag: "809-4fa0224231480"
	Accept-Ranges: bytes
	Content-Length: 2057
	Vary: Accept-Encoding
	Content-Type: text/html
	
	<!DOCTYPE html>
	<html lang="en">
	  <head>
	    <meta charset="utf-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1">
	    <meta name="description" content="">
	    <meta name="author" content="">
	        <link href="http://netdna.bootstrapcdn.com/font-awesome/4.0.3/css/font-awesome.css" rel="stylesheet">
	    <title>Sticky Footer Template for Bootstrap</title>
	
	    <!-- Bootstrap core CSS -->
	    <link href="./css/dashboard-bootstrap.css" rel="stylesheet">
	
	    <!-- Custom styles for this template -->
	    <link href="./css/sticky-footer.css" rel="stylesheet">
	
	    <!-- Just for debugging purposes. Don't actually copy this line! -->
	    <!--[if lt IE 9]><script src="../../assets/js/ie8-responsive-file-warning.js"></script><![endif]-->
	
	    <!-- HTML5 shim and Respond.js IE8 support of HTML5 elements and media queries -->
	    <!--[if lt IE 9]>
	      <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
	      <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
	    <![endif]-->
	  </head>
	
	  <body>
	
	    <!-- Begin page content -->
	    <div class="container">
	      <div class="page-header">
	        <h1>Clash of Classes Dashboard</h1>
	      </div>
	      <p class="lead">This is the Welcome Page for the <b>dashboard</b> section of the service, which is accessible at t
	his URL <a href="http://dashboard.clashofclasses.ch">http://dashboard.clashofclasses.ch</a></p>
	      <p class="lead">You can go back to the <b>live</b> section <a href="http://live.clashofclasses.ch">here</a>.</p>
	
	<p></p>
	        <img src="kid.jpg" width="300">
	<p></p>
	
	
	
	    </div>
	
	    <div id="footer">
	      <div class="container">
	        <p class="text-muted">We <i class="fa fa-heart"></i> Application Level Protocols Teachers</p>
	      </div>
	    </div>
	
	
	    <!-- Bootstrap core JavaScript
	    ================================================== -->
	    <!-- Placed at the end of the document so the pages load faster -->
	  </body>
	</html>

Test sur web-clash-2 - 172.17.0.7

	telnet 172.17.0.7 80
	GET / HTTP/1.1
	HOST:live.clashofclasses.ch
	
	HTTP/1.1 200 OK
	Date: Sat, 24 May 2014 13:30:44 GMT
	Server: Apache/2.4.7 (Ubuntu)
	Last-Modified: Thu, 22 May 2014 19:30:10 GMT
	ETag: "80a-4fa0224231480"
	Accept-Ranges: bytes
	Content-Length: 2058
	Vary: Accept-Encoding
	Content-Type: text/html
	
	<!DOCTYPE html>
	<html lang="en">
	  <head>
	    <meta charset="utf-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1">
	    <meta name="description" content="">
	    <meta name="author" content="">
	        <link href="http://netdna.bootstrapcdn.com/font-awesome/4.0.3/css/font-awesome.css" rel="stylesheet">
	    <title>Sticky Footer Template for Bootstrap</title>
	
	    <!-- Bootstrap core CSS -->
	    <link href="./css/live-bootstrap.css" rel="stylesheet">
	
	    <!-- Custom styles for this template -->
	    <link href="./css/sticky-footer.css" rel="stylesheet">
	
	    <!-- Just for debugging purposes. Don't actually copy this line! -->
	    <!--[if lt IE 9]><script src="../../assets/js/ie8-responsive-file-warning.js"></script><![endif]-->
	
	    <!-- HTML5 shim and Respond.js IE8 support of HTML5 elements and media queries -->
	    <!--[if lt IE 9]>
	      <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
	      <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
	    <![endif]-->
	  </head>
	
	  <body>
	
	    <!-- Begin page content -->
	    <div class="container">
	      <div class="page-header">
	        <h1>Welcome To Clash of Classes!</h1>
	      </div>
	      <p class="lead">This is the Welcome Page for the <b>live</b> section of the website, which is accessible at this U
	RL <a href="http://live.clashofclasses.ch">http://live.clashofclasses.ch</a>.</p>
	      <p class="lead">You can jump to the <b>dashboard</b> section of the website <a href="http://dashboard.clashofclass
	es.ch">here</a>.</p>
	
	        <p></p>
	                <img src="success.jpg" width="300">
	        <p></p>
	
	
	    </div>
	
	
	    <div id="footer">
	      <div class="container">
	        <p class="text-muted">We <i class="fa fa-heart"></i> Application Level Protocols</p>
	      </div>
	    </div>
	
	
	    <!-- Bootstrap core JavaScript
	    ================================================== -->
	    <!-- Placed at the end of the document so the pages load faster -->
	  </body>
	</html>	

	telnet 172.17.0.7 80
	GET / HTTP/1.1
	HOST:leaderboard.clashofclasses.ch

	HTTP/1.1 200 OK
	Date: Sat, 24 May 2014 13:32:03 GMT
	Server: Apache/2.4.7 (Ubuntu)
	Last-Modified: Thu, 22 May 2014 19:30:10 GMT
	ETag: "809-4fa0224231480"
	Accept-Ranges: bytes
	Content-Length: 2057
	Vary: Accept-Encoding
	Content-Type: text/html
	
	<!DOCTYPE html>
	<html lang="en">
	  <head>
	    <meta charset="utf-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1">
	    <meta name="description" content="">
	    <meta name="author" content="">
	        <link href="http://netdna.bootstrapcdn.com/font-awesome/4.0.3/css/font-awesome.css" rel="stylesheet">
	    <title>Sticky Footer Template for Bootstrap</title>
	
	    <!-- Bootstrap core CSS -->
	    <link href="./css/dashboard-bootstrap.css" rel="stylesheet">
	
	    <!-- Custom styles for this template -->
	    <link href="./css/sticky-footer.css" rel="stylesheet">
	
	    <!-- Just for debugging purposes. Don't actually copy this line! -->
	    <!--[if lt IE 9]><script src="../../assets/js/ie8-responsive-file-warning.js"></script><![endif]-->
	
	    <!-- HTML5 shim and Respond.js IE8 support of HTML5 elements and media queries -->
	    <!--[if lt IE 9]>
	      <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
	      <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
	    <![endif]-->
	  </head>
	
	  <body>
	
	    <!-- Begin page content -->
	    <div class="container">
	      <div class="page-header">
	        <h1>Clash of Classes Dashboard</h1>
	      </div>
	      <p class="lead">This is the Welcome Page for the <b>dashboard</b> section of the service, which is accessible at t
	his URL <a href="http://dashboard.clashofclasses.ch">http://dashboard.clashofclasses.ch</a></p>
	      <p class="lead">You can go back to the <b>live</b> section <a href="http://live.clashofclasses.ch">here</a>.</p>
	
	<p></p>
	        <img src="kid.jpg" width="300">
	<p></p>
	
	
	
	    </div>
	
	    <div id="footer">
	      <div class="container">
	        <p class="text-muted">We <i class="fa fa-heart"></i> Application Level Protocols Teachers</p>
	      </div>
	    </div>
	
	
	    <!-- Bootstrap core JavaScript
	    ================================================== -->
	    <!-- Placed at the end of the document so the pages load faster -->
	  </body>
	</html>

Test sur web-clash-3 - 172.17.0.8

	telnet 172.17.0.8 80
	GET / HTTP/1.1
	HOST:live.clashofclasses.ch

	HTTP/1.1 200 OK
	Date: Sat, 24 May 2014 13:32:45 GMT
	Server: Apache/2.4.7 (Ubuntu)
	Last-Modified: Thu, 22 May 2014 19:30:10 GMT
	ETag: "80a-4fa0224231480"
	Accept-Ranges: bytes
	Content-Length: 2058
	Vary: Accept-Encoding
	Content-Type: text/html
	
	<!DOCTYPE html>
	<html lang="en">
	  <head>
	    <meta charset="utf-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1">
	    <meta name="description" content="">
	    <meta name="author" content="">
	        <link href="http://netdna.bootstrapcdn.com/font-awesome/4.0.3/css/font-awesome.css" rel="stylesheet">
	    <title>Sticky Footer Template for Bootstrap</title>
	
	    <!-- Bootstrap core CSS -->
	    <link href="./css/live-bootstrap.css" rel="stylesheet">
	
	    <!-- Custom styles for this template -->
	    <link href="./css/sticky-footer.css" rel="stylesheet">
	
	    <!-- Just for debugging purposes. Don't actually copy this line! -->
	    <!--[if lt IE 9]><script src="../../assets/js/ie8-responsive-file-warning.js"></script><![endif]-->
	
	    <!-- HTML5 shim and Respond.js IE8 support of HTML5 elements and media queries -->
	    <!--[if lt IE 9]>
	      <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
	      <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
	    <![endif]-->
	  </head>
	
	  <body>
	
	    <!-- Begin page content -->
	    <div class="container">
	      <div class="page-header">
	        <h1>Welcome To Clash of Classes!</h1>
	      </div>
	      <p class="lead">This is the Welcome Page for the <b>live</b> section of the website, which is accessible at this U
	RL <a href="http://live.clashofclasses.ch">http://live.clashofclasses.ch</a>.</p>
	      <p class="lead">You can jump to the <b>dashboard</b> section of the website <a href="http://dashboard.clashofclass
	es.ch">here</a>.</p>
	
	        <p></p>
	                <img src="success.jpg" width="300">
	        <p></p>
	
	
	    </div>
	
	
	    <div id="footer">
	      <div class="container">
	        <p class="text-muted">We <i class="fa fa-heart"></i> Application Level Protocols</p>
	      </div>
	    </div>
	
	
	    <!-- Bootstrap core JavaScript
	    ================================================== -->
	    <!-- Placed at the end of the document so the pages load faster -->
	  </body>
	</html>

	telnet 172.17.0.8 80
	GET / HTTP/1.1
	HOST:leaderboard.clashofclasses.ch

	HTTP/1.1 200 OK
	Date: Sat, 24 May 2014 13:33:13 GMT
	Server: Apache/2.4.7 (Ubuntu)
	Last-Modified: Thu, 22 May 2014 19:30:10 GMT
	ETag: "809-4fa0224231480"
	Accept-Ranges: bytes
	Content-Length: 2057
	Vary: Accept-Encoding
	Content-Type: text/html
	
	<!DOCTYPE html>
	<html lang="en">
	  <head>
	    <meta charset="utf-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1">
	    <meta name="description" content="">
	    <meta name="author" content="">
	        <link href="http://netdna.bootstrapcdn.com/font-awesome/4.0.3/css/font-awesome.css" rel="stylesheet">
	    <title>Sticky Footer Template for Bootstrap</title>
	
	    <!-- Bootstrap core CSS -->
	    <link href="./css/dashboard-bootstrap.css" rel="stylesheet">
	
	    <!-- Custom styles for this template -->
	    <link href="./css/sticky-footer.css" rel="stylesheet">
	
	    <!-- Just for debugging purposes. Don't actually copy this line! -->
	    <!--[if lt IE 9]><script src="../../assets/js/ie8-responsive-file-warning.js"></script><![endif]-->
	
	    <!-- HTML5 shim and Respond.js IE8 support of HTML5 elements and media queries -->
	    <!--[if lt IE 9]>
	      <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
	      <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
	    <![endif]-->
	  </head>
	
	  <body>
	
	    <!-- Begin page content -->
	    <div class="container">
	      <div class="page-header">
	        <h1>Clash of Classes Dashboard</h1>
	      </div>
	      <p class="lead">This is the Welcome Page for the <b>dashboard</b> section of the service, which is accessible at t
	his URL <a href="http://dashboard.clashofclasses.ch">http://dashboard.clashofclasses.ch</a></p>
	      <p class="lead">You can go back to the <b>live</b> section <a href="http://live.clashofclasses.ch">here</a>.</p>
	
	<p></p>
	        <img src="kid.jpg" width="300">
	<p></p>
	
	
	
	    </div>
	
	    <div id="footer">
	      <div class="container">
	        <p class="text-muted">We <i class="fa fa-heart"></i> Application Level Protocols Teachers</p>
	      </div>
	    </div>
	
	
	    <!-- Bootstrap core JavaScript
	    ================================================== -->
	    <!-- Placed at the end of the document so the pages load faster -->
	  </body>
	</html>


Nous avons vérifié qu'a chaque fois ce soit le bon contenu qui s'affiche. Nous avons eu les résultats espérés pour les 3 dockers.
# -------------------------------

# -- YOUR ANSWER TO QUESTION 10 --

What procedure did you follow to validate the configuration of 
your complete infrastructure?

Nous avons essayé de nous connecter avec un navigateur. Nous avons également fait du telnet.

Provide details and evidence (command results, etc.) that your 
setup is correct.

Affichage de live.clashofclasses.ch dans un navigateur

![](/img/live.jpg)

Affichage de leaderboard.clashofclasses.ch dans un navigateur

![](/img/leader.jpg)

Telnet :
	
	telnet live.clashofclasses.ch 8014
	GET / HTTP/1.1
	HOST:live.clashoftclasses.ch

	HTTP/1.1 200 OK
	Server: nginx/1.6.0
	Date: Sat, 24 May 2014 15:21:53 GMT
	Content-Type: text/html
	Content-Length: 2060
	Connection: keep-alive
	Last-Modified: Sat, 24 May 2014 15:16:28 GMT
	ETag: "80c-4fa26d4848b00"
	Accept-Ranges: bytes
	Vary: Accept-Encoding
	
	<!DOCTYPE html>
	<html lang="en">
	  <head>
	    <meta charset="utf-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1">
	    <meta name="description" content="">
	    <meta name="author" content="">
	        <link href="http://netdna.bootstrapcdn.com/font-awesome/4.0.3/css/font-a
	wesome.css" rel="stylesheet">
	    <title>Sticky Footer Template for Bootstrap</title>
	
	    <!-- Bootstrap core CSS -->
	    <link href="./css/live-bootstrap.css" rel="stylesheet">
	
	    <!-- Custom styles for this template -->
	    <link href="./css/sticky-footer.css" rel="stylesheet">
	
	    <!-- Just for debugging purposes. Don't actually copy this line! -->
	    <!--[if lt IE 9]><script src="../../assets/js/ie8-responsive-file-warning.js
	"></script><![endif]-->
	
	    <!-- HTML5 shim and Respond.js IE8 support of HTML5 elements and media queri
	es -->
	    <!--[if lt IE 9]>
	      <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></s
	cript>
	      <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js">
	</script>
	    <![endif]-->
	  </head>
	
	  <body>
	
	    <!-- Begin page content -->
	    <div class="container">
	      <div class="page-header">
	        <h1>Welcome To Clash of Classes!</h1>
	      </div>
	      <p class="lead">This is the Welcome Page for the <b>live</b> section of th
	e website, which is accessible at this URL <a href="http://live.clashofclasses.c
	h">http://live.clashofclasses.ch</a>.</p>
	      <p class="lead">You can jump to the <b>dashboard</b> section of the websit
	e <a href="http://leaderboard.clashofclasses.ch">here</a>.</p>
	
	        <p></p>
	                <img src="success.jpg" width="300">
	        <p></p>
	
	
	    </div>
	
	
	    <div id="footer">
	      <div class="container">
	        <p class="text-muted">We <i class="fa fa-heart"></i> Application Level P
	rotocols</p>
	      </div>
	    </div>
	
	
	    <!-- Bootstrap core JavaScript
	    ================================================== -->
	    <!-- Placed at the end of the document so the pages load faster -->
	  </body>
	</html>
	

	telnet leaderboard.clashofclasses.ch 8014
	GET / HTTP/1.1
	HOST:leaderboard.clashoftclasses.ch

	HTTP/1.1 200 OK
	Server: nginx/1.6.0
	Date: Sat, 24 May 2014 15:23:41 GMT
	Content-Type: text/html
	Content-Length: 2060
	Connection: keep-alive
	Last-Modified: Sat, 24 May 2014 15:16:06 GMT
	ETag: "80c-4fa26d334d980"
	Accept-Ranges: bytes
	Vary: Accept-Encoding
	
	<!DOCTYPE html>
	<html lang="en">
	  <head>
	    <meta charset="utf-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1">
	    <meta name="description" content="">
	    <meta name="author" content="">
	        <link href="http://netdna.bootstrapcdn.com/font-awesome/4.0.3/css/font-a
	wesome.css" rel="stylesheet">
	    <title>Sticky Footer Template for Bootstrap</title>
	
	    <!-- Bootstrap core CSS -->
	    <link href="./css/dashboard-bootstrap.css" rel="stylesheet">
	
	    <!-- Custom styles for this template -->
	    <link href="./css/sticky-footer.css" rel="stylesheet">
	
	    <!-- Just for debugging purposes. Don't actually copy this line! -->
	    <!--[if lt IE 9]><script src="../../assets/js/ie8-responsive-file-warning.js
	"></script><![endif]-->
	
	    <!-- HTML5 shim and Respond.js IE8 support of HTML5 elements and media queri
	es -->
	    <!--[if lt IE 9]>
	      <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></s
	cript>
	      <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js">
	</script>
	    <![endif]-->
	  </head>
	
	  <body>
	
	    <!-- Begin page content -->
	    <div class="container">
	      <div class="page-header">
	        <h1>Clash of Classes Dashboard</h1>
	      </div>
	      <p class="lead">This is the Welcome Page for the <b>dashboard</b> section
	of the service, which is accessible at this URL <a href="http://leaderboard.clas
	hofclasses.ch">http://leaderboard.clashofclasses.ch</a></p>
	      <p class="lead">You can go back to the <b>live</b> section <a href="http:/
	/live.clashofclasses.ch">here</a>.</p>
	
	<p></p>
	        <img src="kid.jpg" width="300">
	<p></p>
	
	
	
	    </div>
	
	    <div id="footer">
	      <div class="container">
	        <p class="text-muted">We <i class="fa fa-heart"></i> Application Level P
	rotocols Teachers</p>
	      </div>
	    </div>
	
	    <!-- Bootstrap core JavaScript
	    ================================================== -->
	    <!-- Placed at the end of the document so the pages load faster -->
	  </body>
	</html>
	
	
# -------------------------------