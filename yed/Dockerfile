#
# function yed() {
#  
#  WORKSPACE=${1:-$HOME/Documents/}
#
#  docker run --rm -ti \
#    -e DISPLAY=unix$DISPLAY \
#    -v /tmp/.X11-unix:/tmp/.X11-unix:ro \
#    -v $WORKSPACE:/root/Documents \
#    nberthet/yed
# }
#
# Build: 
#   docker build -t nberthet/yed .
#
FROM nberthet/java-runtime

WORKDIR /opt

RUN apt-get update; apt-get install -y unzip \
 && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
 && curl -LO http://www.yworks.com/resources/yed/demo/yEd-3.16.1.zip \
 && unzip yEd* \
 && rm yEd*.zip

ENTRYPOINT ["java", "-jar", "/opt/yed-3.16.1/yed.jar"]
