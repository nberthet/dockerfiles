#
# Description:
#   Intellij IDEA Community in a container
#
# Usage:
# function usage() {
#  WORKSPACE_ROOT=${1:-/home/${USER}/workspace}
#
#  docker run --rm -ti \
#    -e DISPLAY=unix$DISPLAY \
#    -v /tmp/.X11-unix:/tmp/.X11-unix:ro \
#    -v ${WORKSPACE_ROOT}:/opt/workspace \
#    nberthet/idea
# }
#
# Build: 
#   docker build -t nberthet/idea .

FROM nberthet/java-runtime

WORKDIR /opt

RUN curl -LO https://download-cf.jetbrains.com/idea/ideaIC-2016.2.1.tar.gz \
 && tar xzf idea* \
 && rm -rf idea*.tar.gz

ENTRYPOINT ["/opt/idea-IC-162.1447.26/bin/idea.sh"]
