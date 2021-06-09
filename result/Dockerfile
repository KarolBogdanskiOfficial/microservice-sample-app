FROM node:13-alpine
WORKDIR /result-app

COPY package*.json ./

RUN npm install

COPY server.js .
CMD ["node", "server.js"]