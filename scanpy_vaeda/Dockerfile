#Docker file to see if I can get vaeda (a doublet finder tool) docker running

#Use seurat_scanpy as base image
FROM ksinghal28/seurat_scanpy
ENV DEBIAN_FRONTEND=noninteractive


#Install Python packages

RUN pip3 install numpy
RUN pip3 install pandas
RUN pip3 install scanpy
RUN pip3 install leidenalg
RUN pip3 install decoupler
RUN pip3 install omnipath
RUN pip3 install --upgrade tensorflow==2.8.0
RUN pip3 install --upgrade tensorflow-probability==0.16.0
RUN pip3 install 'scanpy[leiden]'==1.8.0
RUN pip3 install typing-extensions==3.7.4 absl-py==0.10 six==1.15.0 wrapt==1.12.1 xlrd==1.2.0
RUN pip3 install -i https://test.pypi.org/simple/ vaeda==0.0.30


