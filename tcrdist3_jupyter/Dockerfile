#Docker file to run tcrdist3

#Use tcrdist3 quay docker image as base image. (technically 0.2.2 is the newest version but that gives a numpy version error I think because of our server's ubuntu version)
FROM quay.io/kmayerb/tcrdist3:bioRxiv

#Install python packages
RUN pip3 install seaborn
RUN pip3 install natsort
RUN pip3 install "numpy<1.24"

# Install Jupyter Notebook
RUN pip3 install jupyter

# Set up Jupyter Notebook
RUN mkdir /notebooks
WORKDIR /notebooks

# Expose the port Jupyter will run on
EXPOSE 8888

# Start Jupyter Notebook
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]
