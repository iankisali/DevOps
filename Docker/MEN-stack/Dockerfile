FROM node:13-alpine

ENV MONGODB_USERNAME=admin \
    MONGODB_PASSWORD=password

RUN mkdir -p /home/app

COPY . /home/app

CMD ["node", "server.js"]
