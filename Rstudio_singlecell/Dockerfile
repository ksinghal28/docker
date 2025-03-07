FROM ghcr.io/washu-it-ris/rstudio

# Set working directory
WORKDIR /home/rstudio

# Install system dependencies required for various R packages
RUN apt-get update && apt-get install -y --no-install-recommends \
    libxml2-dev \
    libcurl4-openssl-dev \
    libssl-dev \
    libpng-dev \
    libjpeg-dev \
    libcairo2-dev \
    libxt-dev \
    libglpk-dev \
    libgmp3-dev \
    zlib1g-dev \
    libbz2-dev \
    liblzma-dev \
    libhdf5-dev \
    libfftw3-dev \
    libgsl-dev \
    libharfbuzz-dev \
    libfribidi-dev \
    libfontconfig1-dev \
    libfreetype6-dev \
    libpq-dev \
    default-libmysqlclient-dev \
    libsqlite3-dev \
    libv8-dev \
    libicu-dev \
    git \
    cmake \
    python3-dev \
    python3-pip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Installing CRAN packages
RUN R -e 'install.packages(c("remotes", "tidyverse", "dplyr", "Matrix", "stringr", "tibble", \
           "cowplot", "RColorBrewer", "UpSetR", "grid", "heatmap3", "tidyr", "readxl", \
           "ggrepel", "msigdbr", "wordcloud", "gprofiler2"), \
           repos = "https://cloud.r-project.org/", \
           dependencies = TRUE)'

# Install Bioconductor with ask=FALSE parameter to prevent interactive prompts
RUN R -e 'if (!require("BiocManager", quietly = TRUE)) install.packages("BiocManager", repos = "https://cloud.r-project.org/"); \
          BiocManager::install(version = "3.19", ask = FALSE); \
          cat("BiocManager version:", as.character(packageVersion("BiocManager")), "\n")'

# Display R library paths to verify where packages are being installed
RUN R -e '.libPaths()'

# Install all Bioconductor packages at once with ask=FALSE
RUN R -e 'BiocManager::install(c("SingleR", "celldex", "clusterProfiler", "enrichplot", "slingshot", \
          "org.Mm.eg.db", "org.Hs.eg.db", "singleseqgset", "SummarizedExperiment", \
          "DelayedArray", "DelayedMatrixStats", "GenomicRanges"), ask = FALSE)'

# Install Seurat ecosystem packages
RUN R -e 'remotes::install_github("satijalab/seurat", "seurat5", quiet = TRUE)'
RUN R -e 'remotes::install_github("satijalab/seurat-data", "seurat5", quiet = TRUE)'
RUN R -e 'remotes::install_github("satijalab/seurat-wrappers", "seurat5", quiet = TRUE)'

# Install cytotrace2 using remotes
RUN R -e 'remotes::install_github("digitalcytometry/cytotrace2", subdir = "cytotrace2_r")'

# Install monocle3 using remotes
RUN R -e 'remotes::install_github("cole-trapnell-lab/monocle3")'

# Create a directory for data
RUN mkdir -p /home/rstudio/data

# Create a script to check all package installations
RUN echo '# Check all package installations\n\
check_packages <- function() {\n\
  cat("Checking installed packages...\n")\n\
  packages <- c("remotes", "seurat", "Azimuth", "SeuratWrappers", "Signac",\n\
                "tidyverse", "dplyr", "Matrix", "stringr", "tibble", "cowplot",\n\
                "RColorBrewer", "gprofiler2", "UpSetR", "grid", "msigdbr",\n\
                "singleseqgset", "heatmap3", "clusterProfiler", "enrichplot",\n\
                "wordcloud", "org.Mm.eg.db", "org.Hs.eg.db", "tidyr", "readxl",\n\
                "ggrepel", "monocle3", "SingleR", "celldex", "slingshot", "cytotrace2")\n\
                \n\
  installed_pkgs <- rownames(installed.packages())\n\
  missing <- packages[!packages %in% installed_pkgs]\n\
  \n\
  if(length(missing) > 0) {\n\
    cat("Missing packages:", missing, "\n")\n\
  } else {\n\
    cat("All packages successfully installed!\n")\n\
  }\n\
  \n\
  cat("R library paths:", .libPaths(), "\n")\n\
  \n\
  # Show installation locations for key packages\n\
  cat("\\nPackage installation locations:\\n")\n\
  for(pkg in packages) {\n\
    if(pkg %in% installed_pkgs) {\n\
      path <- find.package(pkg)\n\
      cat(pkg, "->", path, "\\n")\n\
    }\n\
  }\n\
}\n\
\n\
check_packages()' > /home/rstudio/check_packages.R

# Set permissions for RStudio user
RUN chown -R rstudio:rstudio /home/rstudio

# Add .Rprofile to set the library path correctly
RUN echo 'cat("Loading personal settings...\\n"); .libPaths(c("/usr/local/lib/R/site-library", .libPaths())); cat("Library paths set to:", .libPaths(), "\\n")' > /home/rstudio/.Rprofile
RUN chown rstudio:rstudio /home/rstudio/.Rprofile

# Expose port 8787 for RStudio
EXPOSE 8787

# Set working directory to RStudio's home
WORKDIR /home/rstudio

