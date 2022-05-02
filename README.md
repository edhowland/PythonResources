# PythonResources
A list of curated (by me) Python resources. Follow me along my Python journey of discovery!

## Abstract

This is a list of Python language resources that I found useful.
This list covers mainly version 3.10, which at the time of this document
was the current stable release of Python.

## Documentation

The main Python docs
- https://docs.python.org/3/

##  Python tutorial videos

Python for Everyone. A 13 hour video from Dr. Chuck (Charles Severance, Ph.D., University of Michigan)

- https://www.youtube.com/watch?v=8DvywoWv6fI

The course website:
- https://www.py4e.com

## CS50P From Harvard

These videos are taught by David J. Malan from the very popular CS50 online course.

Historical note: When David himself took this course back in the day, it was taught by Brian Kernighan.

These videos were shot live. So, there a few glitches. As the CS50 team posts 
edit videos, I will update this list.

Note re: timecodes Where possible, for the multiple lectures we have inserted the start time for each lecture.
We have attempted to give a approximate 1 minute of fudge factor before the lecture start.
If you feel we have errored herein, please fork, fix and do a PR.

CS50P
- Lectures 0, 1 and 2
  - https://youtu.be/TJKnZ784bSI?t=461

  0: This  lecture covers Python's input/output, variables and strings, integers and floats</br>
  1: This lecture covers conditionals and control flow</br>
  2:  Looping</br>

- Lectures 3 and 4
  - https://youtu.be/hpxHkOG6Nyg?t=822
  
  3: Error handling and Exceptions</br>
  4: Libraries including Python's standard libraries</br>  (1:27)

- Lectures 5 and 6
  - https://youtu.be/awVVjpBzuaI?t=730

  5: Unit tests</br>
  6: File input output</br> (1:42)

- Lectures 7
  - https://youtu.be/ENSHLS5DW8A?t=1116

  7: Regular Expressions

## David Beazley videos from various PyCons

Modules and Packaging:
- [https://www.youtube.com/watch?v=bGYZEKstQuQ](https://www.youtube.com/watch?v=bGYZEKstQuQ)

Generators
- [https://www.youtube.com/watch?v=5-qadlG7tWo](https://www.youtube.com/watch?v=5-qadlG7tWo)

Python Meta programming
- [https://www.youtube.com/watch?v=sPiWg5jSoZI](https://www.youtube.com/watch?v=sPiWg5jSoZI)


### Corey Schaefer

These videos are bite-sized between 10-30 minutes long.

The complete Python playlist (143 videos)
- https://youtube.com/playlist?list=PL-osiE80TeTt2d9bfVyTiXJA-UTHn6WwU

A better way to manage Python Virtual Environments with PipEnv
- https://www.youtube.com/watch?v=zDYL22QNiWk

### Trey Hunter

List Comprehensions and generators
- https://www.youtube.com/watch?v=ei71YpmfRX4

List Comprehensions and generators from PyCon 2018
- https://www.youtube.com/watch?v=_6U1XoxyyBY


## Youtube channels

### Tech with Tim
- https://www.youtube.com/c/TechWithTim

### NetworkChuck

This guy drinks WAY too much coffee
- https://www.youtube.com/channel/UC9x0AN7BWHpCDHSm9NiJFJQ

### David Beazley
- https://www.youtube.com/channel/UCbNpPBMvCHr-TeJkkezog7Q

## Books

### By David Beazley

- The Python Cookbook
- Python Distilled
- Python Essentials

Links on Amazon
- https://www.amazon.com/Books-David-Beazley/s?rh=n%3A283155%2Cp_27%3ADavid+Beazley

## Docker Image
You can build your own Docker image to contain the almost latest version of Python.
```bash
docker build -t python:3.10 - <<'eof'
  FROM ubuntu:22.04
  RUN DEBIAN_FRONTEND=noninteractive \
    apt-get update && \
    apt-get install -y python3-pip vim jq
  COPY Dockerfile /
eof
```
Those commands create a Docker image with Python 3, an editor ( vim ), and a JSON query tool ( jq ).

To use the image, use Docker run to launch a container instance.  My preference is to launch the container as a service and then exec into it.
```bash
docker run -d --name python3 python:3.10 sleep inf
docker exec -it python3 /bin/bash
```



## Additional resources


The Python Wiki
- [https://wiki.python.org/moin/](https://wiki.python.org/moin/)


This site seems a bit stale. So, YMMV.
