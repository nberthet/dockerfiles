#
# Description:
#   Eclipse in a container.
# 
# Run: 
# function eclipse() {
#  docker run --rm -ti \
#    -u `id -u`\
#    -e DISPLAY=unix$DISPLAY \
#    -v /tmp/.X11-unix:/tmp/.X11-unix:ro \
#    -v /home/${USER}/.gitconfig:/home/eclipse/.gitconfig:ro \
#    -v /home/${USER}/.ssh:/home/eclipse/.ssh \
#    -v ${WORKSPACE_ROOT}:/home/eclipse/workspace \
#    nberthet/eclipse \
#    -data /home/eclipse/workspace
# }
#
# Build: 
#   docker build -t nberthet/eclipse .

FROM nberthet/java-runtime

WORKDIR /opt

# Although the uid can be overridden, eclipse expects to find this uid in the user file
# which will fail, if there's no such user in the docker image
RUN useradd --shell /bin/bash -d /home/eclipse -u 1000 -o -m eclipse \
 && chown -R eclipse: /home/eclipse \
 && chmod -R ugo+wr /home/eclipse

# Check this page to know how to play with director to install plugins
# http://help.eclipse.org/neon/index.jsp?topic=/org.eclipse.platform.doc.isv/guide/p2_director.html

RUN curl -LO http://eclipse.stu.edu.tw/technology/epp/downloads/release/neon/R/eclipse-java-neon-R-linux-gtk-x86_64.tar.gz \
 && tar xzf eclipse* \
 && rm -rf eclipse*.tar.gz \
 && /opt/eclipse/eclipse -application org.eclipse.equinox.p2.director -noSplash -repository http://beust.com/eclipse -installIUs org.testng.eclipse -d /opt/eclipse \
 && /opt/eclipse/eclipse -application org.eclipse.equinox.p2.director -noSplash -repository http://dist.springsource.org/snapshot/GRECLIPSE/e4.6/ -installIUs org.codehaus.groovy.eclipse.feature.feature.group,org.codehaus.groovy24.feature.feature.group -d /opt/eclipse \
 && /opt/eclipse/eclipse -application org.eclipse.equinox.p2.director -noSplash -repository http://update.eclemma.org/ -installIUs com.mountainminds.eclemma.feature.feature.group -d /opt/eclipse \
 && chown -R eclipse: /opt/eclipse

# Buildship is bundled by default
# RUN /opt/eclipse/eclipse -application org.eclipse.equinox.p2.director -noSplash -repository http://download.eclipse.org/buildship/updates/e46/releases/1.0 -installIU org.eclipse.buildship.feature.group -d /opt/eclipse

WORKDIR /home/eclipse
USER eclipse

ENTRYPOINT ["/opt/eclipse/eclipse"]
