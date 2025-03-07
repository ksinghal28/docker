#Docker file to deepsomatic on compute

#Use their docker image as base image.
FROM google/deepsomatic:1.8.0
ENV DEBIAN_FRONTEND=noninteractive

#Install Python packages

RUN pip3 install absl-py
RUN pip3 install tensorflow

RUN ln -s /opt/deepvariant/bin/deepsomatic/run_deepsomatic /usr/bin/run_deepsomatic

