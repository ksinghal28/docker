FROM satijalab/seurat:5.0.0

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update --fix-missing && apt-get install -y build-essential libcurl4-openssl-dev libxml2-dev libhdf5-dev curl libssl-dev libxml2-dev git python3 jags libfontconfig1-dev r-cran-rjags time && apt-get clean

RUN Rscript -e "install.packages(c('remotes','BiocManager','rsvd'), repo = 'https://cran.wustl.edu/' , dependencies=TRUE)"
RUN Rscript -e "BiocManager::install(c('hexbin','SummarizedExperiment','glmGamPoi','SingleR','celldex','biomaRt','SingleCellExperiment','escape'), ask = FALSE)"
#RUN Rscript -e "devtools::install_github('ncborcherding/escape')"
