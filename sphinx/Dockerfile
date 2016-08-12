#
# Description:
#   sphinx toolset in a container
#   http://www.sphinx-doc.org/
#
# Usage:
#
#   Quickstart:
#   docker run --rm -ti -u `id -u` -v `pwd`:/data nberthet/sphinx sphinx-quickstart
#
#   Make: 
#   docker run --rm -ti -u `id -u` -v `pwd`:/data nberthet/sphinx make html

FROM debian:jessie

RUN apt-get update \
 && apt-get install -y make tar python-pip \
 && pip install Sphinx \
 && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN pip install sphinxcontrib-plantuml \
 && pip install sphinx-intl

WORKDIR /data
VOLUME [ "/data" ]

