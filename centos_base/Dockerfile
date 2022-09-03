# BASE Centos 7 image - used as a starting point by Ansible HOST images
# This image is about ssh server and python3
FROM centos:7
LABEL DevOps Lab Ansible "Elies Jebri elies.jebri@gmail.com"

RUN yum install epel-release -y \
  &&  yum update -y \
  &&  yum install -y openssh-server \
  &&  yum install -y openssh-clients \
  &&  yum install -y python3 \
  &&  yum clean all \
  &&  sed -i 's/#PermitRootLogin yes/PermitRootLogin yes/' /etc/ssh/sshd_config \
  &&  echo 'root:password' | chpasswd \
  &&  mkdir /run/sshd \
  &&  ssh-keygen -A \
  &&  systemctl enable sshd.service --now

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
