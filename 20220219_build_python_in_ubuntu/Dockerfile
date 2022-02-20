FROM ubuntu:latest

ENV PYTHON_VERSION 3.7.1
ENV HOME /root
ENV PYTHON_ROOT $HOME/local/python-$PYTHON_VERSION
ENV PATH $PYTHON_ROOT/bin:$PATH
ENV PYENV_ROOT $HOME/.pyenv

RUN apt update
# RUN apt install -y \
#         git \
#         wget \
#         curl \
#     && git clone https://github.com/pyenv/pyenv.git $PYENV_ROOT \
#     && $PYENV_ROOT/plugins/python-build/install.sh \
#     && /usr/local/bin/python-build -v $PYTHON_VERSION $PYTHON_ROOT \
# RUN rm -rf $PYENV_ROOT

RUN apt install -y python3 python3-pip

RUN pip install --upgrade pip
RUN pip install --upgrade setuptools

WORKDIR /usr/src/app
COPY ./ /usr/src/app

RUN pip install --no-cache-dir -r requirements.txt

# use git
# RUN apt install git-all -y
# RUN npm install https://github.com/Landmaster135/FeedFetcher
# RUN chmod 777 node_modules/feed-fetcher/bin/run
# CMD npm run start


# execute Python code
# RUN python3 app.py
# RUN python3 test/test_helpers.py
# RUN coverage run test/test_helpers.py
# RUN coverage report -m test/test_helpers.py
# RUN coverage html -d coverage_html
