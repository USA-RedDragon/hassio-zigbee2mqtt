ARG BUILD_FROM
FROM $BUILD_FROM

# Add env
ENV LANG C.UTF-8

RUN apk add --update --no-cache jq nodejs nodejs-npm  \
        python2 make gcc g++ linux-headers udev git && \
        git clone -b master --single-branch --depth 1 https://github.com/Koenkk/zigbee2mqtt.git /app

COPY run.sh /app/run.sh

WORKDIR /app

RUN ["chmod", "a+x", "/app/run.sh"]
RUN ["npm", "install", "--unsafe-perm"]
RUN apk del make gcc g++ python2 linux-headers udev git

CMD [ "/app/run.sh" ]