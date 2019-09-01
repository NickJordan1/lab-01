FROM ubuntu

RUN apt-get update
RUN apt-get install -y wget
RUN apt-get install -y sudo

ENV HOSTNAME ubuntu-explore

RUN useradd cmpsc100
RUN mkdir /home/cmpsc100
RUN export HOME=/home/cmpsc100

RUN usermod -p ! root
RUN printf "xpress\nxpress" | sudo passwd cmpsc100
RUN usermod --shell /bin/bash cmpsc100

RUN apt-get update

RUN apt-get install -y less && \
    apt-get install -y nano

ADD https://cs.allegheny.edu/sites/dluman/cmpsc100/pokemon/data.tar.gz /home/cmpsc100/vimpt_data/data.tar.gz

RUN tar -zxvf /home/cmpsc100/vimpt_data/data.tar.gz --directory /home/cmpsc100/vimpt_data/
RUN rm /home/cmpsc100/vimpt_data/data.tar.gz

RUN chown cmpsc100:cmpsc100 /home/cmpsc100 -R

WORKDIR /home/cmpsc100

USER cmpsc100

CMD ["bash"]
