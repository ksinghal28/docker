#Docker file to run R with packages related to single-cell RNA sequencing

#Use Bryan's docker image as base image because haven't been able to get Seurat without it. (Installing Seurat in docker didn't work for me)
#Pulling info from Bryan's conicsmat docker file too

FROM bryanfisk/cytotrace
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y --no-install-recommends build-essential python python3-pip python3-setuptools python3-dev wget cmake libnetcdf-dev libssl-dev libxml2-dev libgdal-dev libudunits2-dev perl git-all

# downloads CONICS
RUN git clone https://github.com/diazlab/CONICS.git

# download samtools
RUN wget https://github.com/samtools/samtools/releases/download/1.12/samtools-1.12.tar.bz2
RUN tar -xf samtools-1.12.tar.bz2

# install samtools
RUN cd samtools-1.12 && make
RUN cd samtools-1.12 && make install

# install bedtools
RUN wget https://github.com/arq5x/bedtools2/releases/download/v2.30.0/bedtools-2.30.0.tar.gz
RUN tar -zxvf bedtools-2.30.0.tar.gz
RUN cd bedtools2 && make

#Install packages

RUN Rscript -e 'install.packages(c("gridExtra", "ggplot2", "scales", "sctransform", "hdf5r", "future", "beanplot", "mixtools", "pheatmap", "zoo", "squash"))'
RUN Rscript -e 'BiocManager::install(c("SingleR", "DropletUtils", "celldex", "biomaRt", "scran"))'
RUN Rscript -e 'devtools::install_github("immunogenomics/harmony")'
RUN Rscript -e 'devtools::install_github("powellgenomicslab/scPred")'
RUN Rscript -e 'remotes::install_github("chris-mcginnis-ucsf/DoubletFinder")'
RUN Rscript -e 'remotes::install_github("satijalab/seurat-wrappers")'
RUN Rscript -e 'devtools::install_github("diazlab/CONICS/CONICSmat", dep = FALSE)'
