FROM armv7/armhf-ubuntu:14.04

MAINTAINER Byeonggil-Jung "jbkcose@gmail.com"

# Config
RUN apt-get update -y
RUN apt-get install -y build-essential openssh-server gdbserver vim

COPY ./output ~/output
WORKDIR ~/output

RUN cp fwup ipmid powerd powertool sensord sensortool ssifd /usr/bin
RUN cp *.so /usr/lib
WORKDIR ../

RUN apt-get install -y ntp
RUN echo 'export TZ="Asia/Seoul"' >> /etc/profile

RUN apt-get install -y git python-pip python-dev postgresql postgresql-server-dev-9.3 libffi-dev
RUN apt-get update -y

# Run daemon
RUN nohup /usr/bin/powerd > /dev/null 2>&1 &
RUN nohup /usr/bin/sensord > /dev/null 2>&1 &
RUN nohup /usr/bin/ipmid > /dev/null 2>&1 &
RUN nohup /usr/bin/ssifd > /dev/null 2>&1 &
