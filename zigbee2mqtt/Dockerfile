ARG BUILD_FROM
FROM $BUILD_FROM

# Add env
ENV LANG C.UTF-8

ENV ZIGBEE2MQTT_VERSION=1.10.2
ENV ARCHIVE=zigbee2mqtt-$ZIGBEE2MQTT_VERSION

RUN apk add --update --no-cache curl jq nodejs npm socat \
    python2 make gcc g++ linux-headers udev git python2 && \
  git clone https://github.com/USA-RedDragon/zigbee2mqtt.git /$ARCHIVE && \
  cd "/$ARCHIVE" && \
  npm install --unsafe-perm -g pm2 && \
  npm install --unsafe-perm && \
  apk del make gcc g++ python2 linux-headers udev && \
  rm -rf docs test images scripts data docker LICENSE README.md update.sh

COPY run.sh "/$ARCHIVE/run.sh"
COPY socat.sh "/$ARCHIVE/socat.sh"
WORKDIR "/$ARCHIVE"

RUN ["chmod", "a+x", "./socat.sh"]
RUN ["chmod", "a+x", "./run.sh"]
CMD [ "./run.sh" ]
