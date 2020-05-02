FROM golang:1.14

# Use mirrors for poor network...
RUN sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list
RUN sed -i 's/security.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list
RUN sed -i 's/deb.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list
# RUN sed -i 's/security.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list


# tiup-cluster dependencies
 RUN apt-get -y -q update && \
     apt-get -y -q install software-properties-common && \
     apt-get install -qqy \
         dos2unix \
         git \
         wget \
         default-mysql-client \
	     vim pssh

RUN  curl --proto '=https' --tlsv1.2 -sSf https://tiup-mirrors.pingcap.com/install.sh | sh 

ADD ./bashrc /root/.bashrc
ADD ./topology.yml /tiup-cluster-example/topology.yml
ADD ./init.sh /init.sh
RUN dos2unix /init.sh /root/.bashrc \
    && chmod +x /init.sh

WORKDIR /tiup-cluster-example

CMD /init.sh
