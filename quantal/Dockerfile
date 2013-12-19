FROM ubuntu:quantal
MAINTAINER Fernando Mayo <fernando@tutum.co>

# Install packages
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -y install openssh-server pwgen
RUN mkdir -p /var/run/sshd && sed -i "s/UsePrivilegeSeparation.*/UsePrivilegeSeparation no/g" /etc/ssh/sshd_config
ADD https://raw.github.com/tutumcloud/tutum-ubuntu/master/set_root_pw.sh /set_root_pw.sh
ADD https://raw.github.com/tutumcloud/tutum-ubuntu/master/run.sh /run.sh
RUN chmod +x /*.sh

# Add tutum motd
RUN rm -f /etc/motd
ADD http://s.tutum.co/motd /etc/motd

EXPOSE 22
CMD ["/run.sh"]
