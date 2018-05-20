FROM ethereum/client-go

RUN apk add --no-cache \
        git \
        bash \
        nodejs \
        yarn

WORKDIR /root

RUN git clone https://github.com/cubedro/eth-net-intelligence-api \
    && cd eth-net-intelligence-api \
    && yarn \
    && yarn global add pm2 --prefix /usr/local

ADD start.sh     /root/start.sh
ADD app.json     /root/eth-net-intelligence-api/app.json
ADD genesis.json /root/files/genesis.json

RUN chmod +x /root/start.sh

VOLUME /root/.ethash/

ENTRYPOINT [ "/root/start.sh" ]