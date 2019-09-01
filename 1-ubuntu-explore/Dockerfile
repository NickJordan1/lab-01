# Build new image from the base Ubuntu image (DockerHub)
FROM ubuntu
# Run update, install missing utilities necessary for image build
RUN apt-get update
RUN apt-get install -y sudo
RUN apt-get install -y wget
# Create the class user
RUN useradd cmpsc100
RUN mkdir /home/cmpsc100
RUN export HOME=/home/cmpsc100
# Seal off access to root
RUN usermod -p ! root
# Give the user a password in case we have to use it
RUN printf "xpress\nxpress" | sudo passwd cmpsc100
# Change the user's shell to /bin/bash on login
RUN usermod --shell /bin/bash cmpsc100
# Update again now that we've installed some packages
RUN apt-get update
# Get less and nano, should we need them; only less matters in my activity
RUN apt-get install -y less && \
    apt-get install -y nano
# Data sourced from: https://github.com/lgreski/pokemonData
ADD https://cs.allegheny.edu/sites/dluman/cmpsc100/pokemon/data.tar.gz /home/cmpsc100/vimpt_data/data.tar.gz
# Untar the data
RUN tar -zxvf /home/cmpsc100/vimpt_data/data.tar.gz --directory /home/cmpsc100/vimpt_data/
# Remove the data
RUN rm /home/cmpsc100/vimpt_data/data.tar.gz
# Give ownership to everything to the class user
RUN chown cmpsc100:cmpsc100 /home/cmpsc100 -R
# Make the working directory the home directory for class user
WORKDIR /home/cmpsc100
# Set the class user as default when login occurs
USER cmpsc100
# Default command, should none be set, is bash
CMD ["bash"]
