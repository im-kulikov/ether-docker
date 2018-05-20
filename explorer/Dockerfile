FROM node:8-alpine

RUN apk add --no-cache \
        git \
        make \
        python \
        g++ \
        yarn

WORKDIR /explorer

RUN git clone https://github.com/etherparty/explorer /explorer \
    && sed -i "s/localhost/0.0.0.0/" package.json \
    && sed -i 's/"prestart": "npm install",//g' package.json \
    && sed -i 's/"postinstall": "bower install",//g' package.json \
    && sed -i "s/localhost:8545/localhost:13545/" app/app.js \
    && yarn \
    && yarn global add bower --prefix /usr/local \
    && bower install --allow-root

EXPOSE 8000

CMD ["yarn", "start"]
