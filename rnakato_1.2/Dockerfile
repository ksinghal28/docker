#Docker file to run R and python with packages related to single-cell RNA sequencing

#Use rnakato shortcake docker image as base image.
FROM rnakato/shortcake:1.2.0
RUN Rscript -e 'install.packages(c("tictoc"))'
