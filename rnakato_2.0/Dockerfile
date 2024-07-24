#Docker file to run R and python with packages related to single-cell RNA sequencing

#Use Bryan's docker image as base image because haven't been able to get Seurat without it. (Installing Seurat in docker didn't work for me)
FROM rnakato/shortcake:2.0.0
RUN Rscript -e 'install.packages(c("tictoc"))'
