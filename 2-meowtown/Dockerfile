# Build new image from the base Ubuntu image (DockerHub)
FROM ubuntu
# Run update, install missing utilities necessary for image build/use
RUN apt-get update
RUN apt-get install -y less
RUN apt-get install -y wget
# Create conditions for /etc/motd to display on terminal connect
RUN echo '[ ! -z "$TERM" -a -r /etc/motd ] && cat /etc/motd' >> /etc/bash.bashrc
# Create the class user
RUN useradd cmpsc100 
RUN mkdir /home/cmpsc100
RUN export HOME=/home/cmpsc100
# Remove find command: NO CHEATING
RUN rm /usr/bin/find
# Get various bash scripts for setting up the rules of the game
ADD https://cs.allegheny.edu/sites/dluman/cmpsc100/.randomize.sh /home/cmpsc100/
ADD https://cs.allegheny.edu/sites/dluman/cmpsc100/.done.sh /home/cmpsc100/
ADD https://cs.allegheny.edu/sites/dluman/cmpsc100/.lab-01-motd /etc/motd
# Give ownership of the bash script for randomization to the class user
RUN chown cmpsc100:cmpsc100 /home/cmpsc100/.randomize.sh -R
# Run the bash script above
RUN cd /home/cmpsc100
RUN bash /home/cmpsc100/.randomize.sh
# Give ownership of /etc/motd to the class user
RUN chown cmpsc100:cmpsc100 /etc/motd
# Set the working directory to the user's home directory
WORKDIR /home/cmpsc100
# Give ownership of the home dir to the class user
RUN chown cmpsc100:cmpsc100 /home/cmpsc100 -R
# Define default command.
CMD ["bash"]
# Set the class user as our default
USER cmpsc100
