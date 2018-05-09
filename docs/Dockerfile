FROM node:8

ENV NODE_ENV production
ENV DEBUG *

WORKDIR /app

COPY package.json /app 

RUN npm install

COPY . /app

EXPOSE 3000

CMD node .