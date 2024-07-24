#Docker file to run tcrdist3

#Use tcrdist3 quay docker image as base image. (technically 0.2.2 is the newest version but that gives a numpy version error I think because of our server's ubuntu version)
FROM quay.io/kmayerb/tcrdist3:bioRxiv

#Install python packages
RUN pip3 install seaborn
RUN pip3 install natsort
RUN pip3 install "numpy<1.24"
