FROM ubuntu:latest

ENV PYTHON_VERSION 3.11.0
ENV HOME /root
ENV PYTHON_ROOT $HOME/local/python-$PYTHON_VERSION
ENV PATH $PYTHON_ROOT/bin:$PATH
ENV PYENV_ROOT $HOME/.pyenv

# setup timezone
RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

# update apt
RUN apt update
# RUN apt install -y \
#         git \
#         wget \
#         curl \
#     && git clone https://github.com/pyenv/pyenv.git $PYENV_ROOT \
#     && $PYENV_ROOT/plugins/python-build/install.sh \
#     && /usr/local/bin/python-build -v $PYTHON_VERSION $PYTHON_ROOT \
# RUN rm -rf $PYENV_ROOT

# for opencv
RUN apt install -y libopencv-dev

# install python and pip
RUN apt install -y python3 python3-pip
RUN pip install --upgrade pip
RUN pip install --upgrade setuptools
# save docker layer cache
WORKDIR /usr/src/app

# save layer cache
COPY ./requirements.txt /usr/src/app/requirements.txt
# save layer cache to make app for neptunus-note repo
# COPY ./generateIssueWf/requirements.txt /usr/src/app/generateIssueWf/requirements.txt

# use git
# RUN apt install git-all -y
RUN apt install git -y
# RUN pip install
# RUN chmod 777 node_modules/feed-fetcher/bin/run
# CMD npm run start

# change working directory to make app for neptunus-note repo
# WORKDIR /usr/src/app/generateIssueWf
# pip install
RUN pip install --no-cache-dir -r requirements.txt

# pip install for test module
COPY ./requirements_test.txt /usr/src/app/requirements_test.txt
RUN pip install --no-cache-dir -r requirements_test.txt

# for tkinter (insufficient)
# RUN apt update
# RUN apt install ubuntu-desktop -y
# RUN apt install python3-tk -y

# install landmasterlibrary
# RUN pip install git+https://github.com/landmaster135/landmasterlibrary.git@main
# RUN pip install -U git+https://github.com/landmaster135/landmasterlibrary.git@main

# install ffmpeg if you wanna use
# RUN apt update
# RUN apt install ffmpeg -y
# RUN ffmpeg -version

# copy files
COPY ./ /usr/src/app
ARG pytest_alias="alias pytest='pytest -n auto'"
RUN echo ${pytest_alias} >> ~/.bashrc
ARG python_app_run="alias pa='python3 app.py'"
RUN echo ${python_app_run} >> ~/.bashrc

# execute Python code
# RUN python3 app.py
# RUN python3 test/test_helpers.py
# RUN python3 test.test_helpers
# RUN python3 -m unittest test.test_helpers
# RUN coverage run test/test_helpers.py
# RUN coverage report -m test/test_helpers.py
# RUN coverage html -d coverage_html
