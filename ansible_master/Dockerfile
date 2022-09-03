# Ansible Base image with ssh access - used as a starting point by Ansible MASTER images
# This image is about Ansible and ssh server
# Centos 7
FROM centos:7
LABEL DevOps Lab Ansible "Elies Jebri elies.jebri@gmail.com"

RUN yum install epel-release -y \
  &&  yum update -y \
  &&  yum install -y openssh-server \
  &&  yum install -y openssh-clients \
  &&  yum install ansible -y \
  &&  yum clean all \
  &&  sed -i 's/#PermitRootLogin yes/PermitRootLogin yes/' /etc/ssh/sshd_config \
  &&  echo 'root:password' | chpasswd \
  &&  mkdir /run/sshd \
  &&  ssh-keygen -A \
  &&  systemctl enable sshd.service --now

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
