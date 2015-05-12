tutum-ubuntu
============

[![Deploy to Tutum](https://s.tutum.co/deploy-to-tutum.svg)](https://dashboard.tutum.co/stack/deploy/)

Simple Ubuntu docker images with SSH access


Usage
-----

To create the image `tutum/ubuntu` with one tag per Ubuntu release,
execute the following commands on the tutum-ubuntu branch:

	docker build -t tutum/ubuntu:latest .
	docker build -t tutum/ubuntu:lucid lucid/
	docker build -t tutum/ubuntu:precise precise/
	docker build -t tutum/ubuntu:trusty trusty/
	docker build -t tutum/ubuntu:utopic utopic/
	docker build -t tutum/ubuntu:vivid vivid/


Running tutum/ubuntu
--------------------

To run a container from the image you created earlier with the `trusty` tag
binding it to port 2222 in all interfaces, execute:

	docker run -d -p 0.0.0.0:2222:22 tutum/ubuntu:trusty

The first time that you run your container, a random password will be generated
for user `root`. To get the password, check the logs of the container by running:

	docker logs <CONTAINER_ID>

You will see an output like the following:

	========================================================================
	You can now connect to this Ubuntu container via SSH using:

	    ssh -p <port> root@<host>
	and enter the root password 'U0iSGVUCr7W3' when prompted

	Please remember to change the above password as soon as possible!
	========================================================================

In this case, `U0iSGVUCr7W3` is the password allocated to the `root` user.

Done!


Setting a specific password for the root account
------------------------------------------------

If you want to use a preset password instead of a random generated one, you can
set the environment variable `ROOT_PASS` to your specific password when running the container:

	docker run -d -p 2222:22 -e ROOT_PASS="mypass" tutum/ubuntu:trusty


Adding SSH authorized keys
--------------------------

If you want to use your SSH key to login, you can use `AUTHORIZED_KEYS` environment variable. You can add more than one public key separating them by `,`:

    docker run -d -p 2222:22 -e AUTHORIZED_KEYS="`cat ~/.ssh/id_rsa.pub`" tutum/ubuntu:trusty
