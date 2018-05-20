FROM node:8-alpine

RUN apk add --no-cache \
        git \
        yarn

WORKDIR /netstats

RUN git clone --depth 1 \
        https://github.com/cubedro/eth-netstats /netstats \
    && sed -i 's/"node": "0.12.0",//g' package.json \
    && sed -i 's/ "npm": "2.5.1"//g' package.json \
    && yarn \
    && yarn global add grunt-cli --prefix /usr/local \
    && grunt

EXPOSE 3000

CMD ["yarn", "start"]
