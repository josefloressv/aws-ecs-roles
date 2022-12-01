FROM alpine:latest

RUN apk add --no-cache nodejs npm

WORKDIR /app
COPY package.json /app
COPY package-lock.json /app
COPY app.js /app

RUN npm install

EXPOSE 3000
CMD ["npm", "start"]
