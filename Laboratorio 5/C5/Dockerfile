FROM ubuntu:20.10

COPY sources.list /etc/apt/sources.list

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y build-essential wget zlib1g-dev libssl-dev

# Instalar OpenSSH Portable 8.3
RUN wget https://cdn.openbsd.org/pub/OpenBSD/OpenSSH/portable/openssh-8.3p1.tar.gz && \
    tar zxvf openssh-8.3p1.tar.gz

# Modificar la version a ?
RUN sed -i '3s/8.3/?/' /openssh-8.3p1/version.h
WORKDIR /openssh-8.3p1

# Buildear desde source
RUN ./configure && \
    make && \
    make install

CMD ["bash"]
