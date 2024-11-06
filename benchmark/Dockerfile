FROM python:3.10-bullseye
RUN apt-get update
RUN apt-get install -y less git build-essential wget
RUN echo "deb http://binaries2.erlang-solutions.com/debian/ bullseye-esl-erlang-26 contrib" | tee -a /etc/apt/sources.list
RUN wget https://binaries2.erlang-solutions.com/GPG-KEY-pmanager.asc
RUN apt-key add GPG-KEY-pmanager.asc
RUN apt-get update
RUN apt-get install -y esl-erlang
RUN wget https://s3.amazonaws.com/rebar3/rebar3
RUN chmod +x rebar3
RUN ./rebar3 local install
RUN export PATH=$PATH:${HOME}/.cache/rebar3/bin
COPY . /aider
RUN pip install --no-cache-dir --upgrade pip
RUN pip install --no-cache-dir -e /aider[dev]
RUN git config --global --add safe.directory /aider
WORKDIR /aider
