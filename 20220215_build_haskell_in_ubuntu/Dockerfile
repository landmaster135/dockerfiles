FROM ubuntu:latest

# RUN apt update
RUN apt update

# for install n
# RUN apt install -y curl

# decide working directory
WORKDIR /usr/app

# install Haskell
RUN apt -y install haskell-platform


# In case with Haskell Stack: Start -----------------------

# install Haskell Stack (プロジェクト管理機能も備える)
RUN apt -y install haskell-stack
RUN stack upgrade
RUN echo "export PATH=$HOME/.local/bin:$PATH" >> ~/.bashrc
RUN source ~/.bashrc
RUN stack setup

# use Haskell Stack
# RUN stack new sample
# RUN cd ./sample
# RUN stack build
# RUN stack run

# In case with Haskell Stack: End -----------------------


# copy files in the current directory to directory in the built container.
COPY ./ /usr/app

# execute Haskell
RUN ghc Hello.hs
# RUN ./Hello

# execute Haskell like a script file.
# RUN runghc Hello.hs
