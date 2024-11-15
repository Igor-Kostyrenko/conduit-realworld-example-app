# backend/Dockerfile
FROM node:18-alpine

WORKDIR /app
COPY package*.json ./
RUN apk update && apk add postgresql-client && apk add --no-cache bash
RUN npm install

COPY . .

ADD https://raw.githubusercontent.com/vishnubob/wait-for-it/master/wait-for-it.sh /wait-for-it.sh
RUN chmod +x /wait-for-it.sh

EXPOSE 3001

CMD ["sh", "-c", "/wait-for-it.sh postgres:5432 -- npm run dev"]
