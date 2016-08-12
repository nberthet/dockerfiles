#
# Description:
#   GraphViz in Docker
#
#   dot is used as entrypoint
#
# Usage:
#   docker run --rm -i nberthet/dot -Tpng < input.dot > output.png
#
FROM debian:jessie
MAINTAINER Nicolas Berthet

RUN apt-get update ;\
    apt-get install -y graphviz ;\
    apt-get clean ;\
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ENTRYPOINT [ "/usr/bin/dot" ]
