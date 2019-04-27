FROM sugartensor/sugartensor:1.0.0.2-cpu
MAINTAINER Namju Kim namju.kim@kakaocorp.com

# ffmpeg requirements
RUN add-apt-repository ppa:mc3man/trusty-media
RUN apt-get update
RUN apt-get dist-upgrade -y
RUN apt-get -y install ffmpeg

# requirements
RUN pip install --upgrade pip
RUN pip install pandas==0.19.2
RUN pip install librosa==0.5.0
#RUN pip install scikits.audiolab==0.11.0

# copy pre-trained weight and some sample audio data
RUN mkdir -p /root/stt/
RUN mkdir -p /root/stt/asset/data/LibriSpeech/test-clean/1089/134686
RUN mkdir -p /root/stt/asset/train
ADD *.py /root/stt/
ADD asset/train/checkpoint /root/stt/asset/train/
ADD asset/train/model.ckpt-205919* /root/stt/asset/train/
ADD asset/data/LibriSpeech/test-clean/1089/134686/* /root/stt/asset/data/LibriSpeech/test-clean/1089/134686/

# set default directory
WORKDIR /root/stt

# default entry point
ENTRYPOINT bash


