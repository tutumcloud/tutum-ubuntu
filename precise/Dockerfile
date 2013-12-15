FROM ubuntu:precise
MAINTAINER Fernando Mayo <fernando@tutum.co>

# Install packages
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -y install openssh-server && mkdir -p /var/run/sshd && echo 'root:changeme' | chpasswd
RUN sed -i "s/UsePrivilegeSeparation.*/UsePrivilegeSeparation no/g" /etc/ssh/sshd_config

# Add tutum motd
RUN rm -f /etc/motd
ADD http://s.tutum.co/motd /etc/motd

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
