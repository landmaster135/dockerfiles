FROM ubuntu:latest

# RUN apt-get update
# RUN apt update
ENV PYTHON_VERSION 3.7.1
ENV HOME /root
ENV PYTHON_ROOT $HOME/local/python-$PYTHON_VERSION
ENV PATH $PYTHON_ROOT/bin:$PATH
ENV PYENV_ROOT $HOME/.pyenv
RUN apt update && apt upgrade -y \
    && apt install -y \
        git \
        make \
        build-essential \
        libssl-dev \
        zlib1g-dev \
        libbz2-dev \
        libreadline-dev \
        libsqlite3-dev \
        wget \
        curl \
        llvm \
        libncurses5-dev \
        libncursesw5-dev \
        xz-utils \
        tk-dev \
        libffi-dev \
        liblzma-dev \
    && git clone https://github.com/pyenv/pyenv.git $PYENV_ROOT \
    && $PYENV_ROOT/plugins/python-build/install.sh \
    && /usr/local/bin/python-build -v $PYTHON_VERSION $PYTHON_ROOT \
    && rm -rf $PYENV_ROOT

RUN pip install --upgrade pip
RUN pip install --upgrade setuptools
# # for install n
# RUN apt install -y curl

# # install old nodejs and npm
# RUN apt install nodejs -y
# RUN apt install npm -y

# # for version up nodejs
# RUN npm install -g n
# RUN n 16.13.1

# # uninstall old nodejs and npm
# RUN apt purge nodejs npm -y

# # for version up npm
# RUN npm install -g npm
# RUN npm update -g




# to avoid "npm ERR! Tracker "idealTree" already exists"
WORKDIR /usr/src/app
COPY ./ /usr/src/app

RUN pip install --no-cache-dir -r requirements.txt

# use git
# RUN apt install git-all -y
# RUN npm install https://github.com/Landmaster135/FeedFetcher
# RUN chmod 777 node_modules/feed-fetcher/bin/run
# CMD npm run start

