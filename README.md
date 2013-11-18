tutum-ubuntu
============

Simple ubuntu docker image with SSH access


Usage
-----

To create the image `tutum/ubuntu`, execute the following command on the tutum-ubuntu folder:

	docker build -t tutum/ubuntu .


Running tutum/ubuntu
--------------------

Run a container from the image you created earlier:

	sudo docker run -d -p 0.0.0.0::22 tutum/ubuntu


It will print the new container ID (like `d35bf1374e88`). Get the allocated external port:

	sudo docker port d35bf1374e88 22


It will print the allocated port (like 0.0.0.0:4751). Test your deployment:

	ssh -p 4751 root@localhost

Use `changeme` as the initial password.

Enjoy!
