FROM cypress/browsers:chrome62

USER root

RUN set -ex && \
    echo 'deb http://deb.debian.org/debian jessie-backports main' \
      > /etc/apt/sources.list.d/jessie-backports.list && \

    apt update -y && \
    apt install -t \
      jessie-backports \
      openjdk-8-jre-headless \
      ca-certificates-java -y

ENV npm_config_loglevel=warn

RUN npm install -g cypress@1.0.2

ADD xvfb.init /etc/init.d/xvfb
RUN chmod +x /etc/init.d/xvfb
RUN update-rc.d xvfb defaults

CMD ["cypress", "run"]
