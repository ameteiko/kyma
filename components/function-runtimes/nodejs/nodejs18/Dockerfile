# image base on node:lts-alpine3.17 (node:18.14.2, alpine:3.17.2)
FROM node@sha256:fdbd2737cb94e25cae3db9fc5d7dc073c9675dad34239bfb3948c499a6908c19

ARG NODE_ENV
ENV NODE_ENV $NODE_ENV
ENV npm_config_cache /tmp/

RUN mkdir -p /usr/src/app
RUN mkdir -p /usr/src/app/lib
WORKDIR /usr/src/app

COPY ./nodejs18/package.json /usr/src/app/
RUN npm install && npm cache clean --force
COPY ./lib /usr/src/app/lib

COPY ./server.js /usr/src/app/server.js

CMD ["npm", "start"]

EXPOSE 8888
