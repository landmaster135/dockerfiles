FROM ubuntu:latest

# RUN apt-get update
RUN apt update

# for install n
RUN apt install -y curl

# install old nodejs and npm
RUN apt install nodejs -y
RUN apt install npm -y

# for version up nodejs
RUN npm install -g n
RUN n 16.13.1

# uninstall old nodejs and npm
RUN apt purge nodejs npm -y

# for version up npm
RUN npm install -g npm
RUN npm update -g

# to avoid "npm ERR! Tracker "idealTree" already exists"
WORKDIR /usr/app
COPY ./ /usr/app

# not need "update-alternatives" if "n" package manager
# RUN update-alternatives --install /usr/bin/node node /usr/bin/nodejs 10

# to get files from local
ADD README.md .

# use git
# RUN apt install git-all -y
# RUN npm install https://github.com/Landmaster135/FeedFetcher
# RUN chmod 777 node_modules/feed-fetcher/bin/run
# CMD npm run start