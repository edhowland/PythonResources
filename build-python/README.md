# Building Python from source

## Abstract

A simpler, pragmatic approach to managing multiple Python versions and environments.
Even though there are quite a few   tools to manage multiple Python environments,
such as pyenv, pipenv, virtualenv .etc, they require a consider investment
of time and system resources. Here we take Herr Prof. Einstein's advice: 
Things should be as simple  as possible and no more.


## Background

My system currently consists of the following things:

- Ubuntu 18.04 Linux
- Installed Pythons (managed by 'apt')
  * python : 2.7.17
  * python3 : 3.6.9
- python-launcher


Note: python-launcher is also abbreviated as  'py'.
When you type 'py' in place of 'python', you get the maximal version according to semver.
Currently, that is '3.6.9'

Good advice I've read or listened to online is to not use the built in system
python, but use the latest python alongside it.

There are several approaches to this.

- Use 'pyenv' to manage multiple Python versions.
- Use some apt ppa such as 'dead snakes'
- Use Docker

My needs are simpler than than those of serious Python developers.
I just need a single extra current stable Python release. (Currently 3.10.4)
With that version in my $PATH, 'py' will default to it every time I need to invoke
a Python script.

## Building latest Python

This document and Docker files and scripts help automate the process of
downloading the source of the latest version of Python (called C Python)
uncompressing it and then using compiler tools to build it using a Docker container.
This docker image is called ubuntu-dev.
After the entire package has been built, then the 'ubuntu-dev' image is  no longer
needed and can be removed.


## Note re: Python source

The source is delivered in a xz compressed tarball.
This requires adjustment to the ubuntu-dev image (E.g. apt-get install -y xz-utils)
and the actual tar extraction.


```bash
tar -x -J -f Python-3.10.4.tar.xz
```

### Starting the docker container

```bash
docker run --rm -it -v${PWD}:/work -v ${HOME}/.local/opt:/opt ubuntu-dev /bin/bash 
```


```bash
# Here we are inside the running Docker container from ubuntu-dev
cd /work
./configure --enable-optimizations --prefix=/opt/python-3.10.4
make install
```


## Sample Dockerfile to set user for build environment

```Dockerfile
FROM ubuntu:xenial-20170214
ARG UNAME=testuser
ARG UID=1000
ARG GID=1000
RUN groupadd -g $GID -o $UNAME
RUN useradd -m -u $UID -g $GID -o -s /bin/bash $UNAME
USER $UNAME
CMD /bin/bash

```


## The docker build command

```bash

docker build --build-arg UID=$(id -u) --build-arg GID=$(id -g)   -f bb.dockerfile -t testimg .

```


## Conclusion

After the latest Python version has been compiled and installed, and your $PATH
has beed appended with ~/.local/opt/python-3.10.4/bin, use of the 'py' command
will find and use this version.

### Note about pip

At this point, 'pip3' is still your original python3 version.
To use the correct version with python 3.10.4, use an alternate version
of invocation:

```bash
py -m pip install requests
```

I have aliased the above to:

```bash
alias pypip='py -m pip'
```

