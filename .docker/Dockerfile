FROM        php:apache

ARG         USER_ID
ARG         GROUP_ID

RUN         addgroup --gid $GROUP_ID dockeruser
RUN         adduser --disabled-password --gecos '' --uid $USER_ID --gid $GROUP_ID dockeruser
USER        dockeruser