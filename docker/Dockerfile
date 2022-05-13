FROM ubuntu:22.04
RUN DEBIAN_FRONTEND=noninteractive \
    apt-get update && \
    apt-get install -y python3-pip vim jq
# install python packages: pytest: for testing, black: linting/formatting,
#    mypy: type checking, sphinx: documentation creation
RUN pip3 install pytest black mypy sphinx
COPY Dockerfile /
