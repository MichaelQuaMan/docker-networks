FROM ubuntu:latest

RUN apt-get update && apt-get install -y \
    iptables \
    libltdl7 \
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

RUN mkdir /root/.ssh /var/run/sshd \ 
  && dpkg -i /app/packages/*.deb \
  && mv /app/certs/* /root/.ssh/ \
  && mv /app/conf/sshd_config /etc/ssh \
  && chmod 600 /root/.ssh/id_rsa 

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]

