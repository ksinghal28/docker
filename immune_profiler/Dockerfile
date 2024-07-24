#Docker file to run Immune Profiler python package

#Use Bryan's docker image as base image because it has python
FROM rappdw/docker-java-python:openjdk1.8.0_171-python3.6.6
ENV DEBIAN_FRONTEND=noninteractive


#Install Python packages

RUN pip3 install numpy
RUN pip3 install pandas
RUN pip3 install argparse
RUN pip3 install python-csv
RUN pip3 install openpyxl
RUN pip3 install matplotlib
RUN pip3 install biopython
