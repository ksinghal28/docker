#Docker file to run R and python with packages related to single-cell RNA sequencing

#Use Bryan's docker image as base image because haven't been able to get Seurat without it. (Installing Seurat in docker didn't work for me)
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


#Install R packages

RUN Rscript -e 'install.packages(c("gridExtra", "ggplot2", "scales", "sctransform", "hdf5r", "future", "beanplot", "mixtools", "pheatmap", "zoo", "squash", "reticulate", "anndata"))'
RUN Rscript -e 'BiocManager::install(c("SingleR", "DropletUtils", "celldex", "biomaRt", "scran", "scDblFinder", "SingleCellExperiment", "scater"))'
RUN Rscript -e 'devtools::install_github("immunogenomics/harmony")'
RUN Rscript -e 'devtools::install_github("powellgenomicslab/scPred")'
RUN Rscript -e 'remotes::install_github("chris-mcginnis-ucsf/DoubletFinder")'
RUN Rscript -e 'remotes::install_github("satijalab/seurat-wrappers")'
RUN Rscript -e 'devtools::install_github("diazlab/CONICS/CONICSmat", dep = FALSE)'

#Install Python packages

RUN pip3 install numpy
RUN pip3 install pandas
RUN pip3 install scanpy
RUN pip3 install leidenalg
RUN pip3 install decoupler
RUN pip3 install omnipath
RUN pip3 install anndata2ri
RUN pip3 install rpy2
