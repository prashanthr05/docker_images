FROM robotology/yarp:master
MAINTAINER Diego Ferigo <diego.ferigo@iit.it>

# Install tools
RUN apt-get update &&\
    apt-get install -y --no-install-recommends \
        wget &&\
    rm -rf /var/lib/apt/lists/*

# Install gazebo7
RUN echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" \
        > /etc/apt/sources.list.d/gazebo-stable.list &&\
    wget http://packages.osrfoundation.org/gazebo.key -O - | apt-key add - &&\
    apt-get update &&\
    apt-get install -y --no-install-recommends \
        gazebo7 \
        gazebo7-plugin-base \
        libgazebo7-dev &&\
    rm -rf /var/lib/apt/lists/*

# Include a custom entrypoint script
COPY entrypoint.sh /usr/sbin/entrypoint.sh
RUN chmod 755 /usr/sbin/entrypoint.sh
ENTRYPOINT ["/usr/sbin/entrypoint.sh"]
