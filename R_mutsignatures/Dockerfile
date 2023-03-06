#Docker file to run R with packages related to single-cell RNA sequencing

#Use Bryan's docker image as base image because it has R
FROM bryanfisk/cytotrace
ENV DEBIAN_FRONTEND=noninteractive


#Install packages

RUN Rscript -e 'install.packages(c("gridExtra", "ggplot2", "ggrepel", "dplyr", "tidyverse", "readxl", "reshape2", "kableExtra"))'

RUN Rscript -e 'devtools::install_github("dami82/mutSignatures")'

RUN Rscript -e 'BiocManager::install("BSgenome.Hsapiens.UCSC.hg38")'