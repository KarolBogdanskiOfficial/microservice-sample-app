FROM node:12.18-alpine

ENV NODE_ENV=production
WORKDIR /opt

COPY package*.json, ./
RUN npm install --production --silent && mv node_modules ../

COPY . .

EXPOSE 3000

CMD ["node", "server.js"]
