FROM ubuntu
# installation
RUN apt-get update
RUN apt-get -y install zip
RUN apt-get -y install unzip
RUN apt-get install -y git
RUN apt-get install python3.7

# INTALL CONDA

ENV PATH="/root/miniconda3/bin:${PATH}"
ARG PATH="/root/miniconda3/bin:${PATH}"
RUN apt-get update

RUN apt-get install -y wget && rm -rf /var/lib/apt/lists/*

RUN wget \
    https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh \
    && mkdir /root/.conda \
    && bash Miniconda3-latest-Linux-x86_64.sh -b \
    && rm -f Miniconda3-latest-Linux-x86_64.sh 

WORKDIR /usr/src/app

COPY install.sh .
COPY requirements.txt .
COPY download_bert_model.py .
RUN sh ./install.sh

# get python files for the demo

RUN git clone https://github.com/Shaul1321/covid-ai2 #redo

WORKDIR /usr/src/app/covid-ai2
RUN ls
# download data & run streamlit
COPY startup.sh .
RUN ls
CMD ["bash", "startup.sh"]
