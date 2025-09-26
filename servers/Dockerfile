FROM ubuntu:22.04
RUN apt-get update && apt-get install -y openssh-server sudo git curl \
 && mkdir /var/run/sshd \
 && useradd -m -s /bin/bash devops \
 && echo 'devops ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/devops \
 && chmod 440 /etc/sudoers.d/devops \
 && mkdir -p /home/devops/.ssh \
 && chmod 700 /home/devops/.ssh
# Autorise l'auth par clé et par mot de passe
RUN sed -ri 's/^#?PasswordAuthentication .*/PasswordAuthentication yes/' /etc/ssh/sshd_config \
 && sed -ri 's/^#?PermitRootLogin .*/PermitRootLogin no/' /etc/ssh/sshd_config
EXPOSE 22
CMD ["/usr/sbin/sshd","-D","-e"]
