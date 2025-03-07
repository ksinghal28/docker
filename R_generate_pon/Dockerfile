#Docker file to run R with packages related to single-cell RNA sequencing

#Use Bryan's docker image as base image because haven't been able to get Seurat without it. (Installing Seurat in docker didn't work for me)
FROM bryanfisk/cytotrace
ENV DEBIAN_FRONTEND=noninteractive


#Install packages

RUN Rscript -e 'install.packages(c("gridExtra", "ggplot2", "scales", "sctransform", "hdf5r", "future", "dplyr", "data.table", "vcfR", "ComplexUpset"))'
