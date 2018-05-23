FROM node:8

ENV NODE_ENV development

#Uncomment the next hastag and allow docker to initiate debug
#ENV DEBUG *

WORKDIR /app

COPY package.json /app 

RUN npm install

COPY . /app

EXPOSE 3000

CMD node .