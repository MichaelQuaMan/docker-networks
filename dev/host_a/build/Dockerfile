FROM ubuntu:latest

RUN apt-get update --fix-missing && apt-get install -y \
    tcpdump \
    vim \
    openssh-client \
    openssh-server \
    sshfs \
    traceroute \
    dnsutils \
    netcat-openbsd \
    nmap \
    net-tools \ 
    iproute2 \
    iputils-ping \
    curl \
  && rm -rf /var/lib/apt/lists/*

COPY app/ /app/ 

ENV NOTVISIBLE "in users profile"

RUN mkdir /root/.ssh /var/run/sshd \ 
  && mv /app/certs/* /root/.ssh/ \
  && mv /app/conf/sshd_config /etc/ssh \
  && chmod 600 /root/.ssh/id_rsa 
  #&& echo 'root:screencast' | chpasswd \
  #&& sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config \
  #&& sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd \
  #&& echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
