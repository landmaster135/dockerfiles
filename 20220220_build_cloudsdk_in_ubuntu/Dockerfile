FROM ubuntu:latest

RUN apt update

WORKDIR /usr/src/app
COPY ./ /usr/src/app

# prepare setting up Cloud-SDK
RUN apt install apt-transport-https ca-certificates gnupg -y
RUN echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] http://packages.cloud.google.com/apt cloud-sdk main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
RUN apt install -y curl
RUN curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -
RUN apt update
RUN apt install -y python3 python3-pip

# setup Cloud-SDK
RUN apt update && apt install google-cloud-sdk -y
