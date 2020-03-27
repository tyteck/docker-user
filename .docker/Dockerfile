FROM        php:apache

#ARG         USER_ID
#ARG         GROUP_ID

RUN     apt-get update -y && \
        apt-get install -yqq supervisor && \
        rm -rf /var/lib/apt/lists/*;

# creating appropriate user
#RUN         addgroup --gid $GROUP_ID dockeruser
#RUN         adduser --disabled-password --gecos '' --uid $USER_ID --gid $GROUP_ID dockeruser

COPY        ./run-on-start.sh /etc/init.d/run-on-start.sh

CMD     ["/etc/init.d/run-on-start.sh"]

#USER        dockeruser