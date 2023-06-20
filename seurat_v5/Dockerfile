#Docker file for seurat v5

#Use singlecell_big as base image (tag1.3 as of making this docker)
FROM ksinghal28/singlecell_big
ENV DEBIAN_FRONTEND=noninteractive


#Install packages

RUN Rscript -e 'install.packages(c("gridExtra", "ggplot2", "scales", "sctransform", "hdf5r", "future"))'
RUN Rscript -e 'BiocManager::install(c("SingleR", "DropletUtils", "celldex"))'
RUN Rscript -e 'devtools::install_github("immunogenomics/harmony")'
RUN Rscript -e 'devtools::install_github("powellgenomicslab/scPred")'
RUN Rscript -e 'remotes::install_github("satijalab/seurat", "seurat5", quiet=TRUE)'
RUN Rscript -e 'remotes::install_github("satijalab/seurat-wrappers")'
RUN Rscript -e 'remotes::install_github("satijalab/seurat-data", "seurat5", quiet = TRUE)'
RUN Rscript -e 'remotes::install_github("satijalab/azimuth", "seurat5", quiet = TRUE)'
RUN Rscript -e 'remotes::install_github("satijalab/seurat-wrappers", "seurat5", quiet = TRUE)'
RUN Rscript -e 'remotes::install_github("stuart-lab/signac", "seurat5", quiet = TRUE)'
RUN Rscript -e 'remotes::install_github("bnprks/BPCells", quiet = TRUE)'


