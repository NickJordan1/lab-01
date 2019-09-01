FROM ubuntu

RUN apt-get update

RUN apt-get install -y wget

RUN apt-get install -y less

RUN echo '[ ! -z "$TERM" -a -r /etc/motd ] && cat /etc/motd' >> /etc/bash.bashrc

RUN useradd cmpsc100 
RUN mkdir /home/cmpsc100
RUN export HOME=/home/cmpsc100

RUN rm /usr/bin/find

ADD https://cs.allegheny.edu/sites/dluman/cmpsc100/.randomize.sh /home/cmpsc100/
ADD https://cs.allegheny.edu/sites/dluman/cmpsc100/.done.sh /home/cmpsc100/
ADD https://cs.allegheny.edu/sites/dluman/cmpsc100/.lab-01-motd /etc/motd
RUN chown cmpsc100:cmpsc100 /home/cmpsc100/.randomize.sh -R
RUN cd /home/cmpsc100
RUN bash /home/cmpsc100/.randomize.sh

RUN chown cmpsc100:cmpsc100 /etc/motd

WORKDIR /home/cmpsc100

RUN chown cmpsc100:cmpsc100 /home/cmpsc100 -R

# Define default command.
CMD ["bash"]

USER cmpsc100
