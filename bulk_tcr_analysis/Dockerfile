#Docker file to run R and python with packages related to single-cell RNA sequencing

#Use their docker image as base image . (Installing directly in my existing docker didn't work for me)
FROM immunomind/immunarch-docker:0.9.0
ENV DEBIAN_FRONTEND=noninteractive

#Install R packages

RUN Rscript -e 'install.packages(c("gridExtra", "ggplot2", "scales","reticulate", "ggalluvial", "ggvenn", "tidyverse"))'


