FROM node:11-alpine

ENV NODE_VERSION 12.16.1

WORKDIR /code/

COPY . .

RUN npm install

EXPOSE 80

CMD ["npm", "run", "start"]