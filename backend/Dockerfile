FROM node:17.5.0-alpine3.14

ARG UID=1001
WORKDIR /srv/app

RUN adduser --disabled-password --uid "$UID" app

COPY [ "package.json", "package-lock.json",  "./"]
RUN npm install

COPY [ "config", "config"]
COPY [ "src", "src"]

RUN npm run build

EXPOSE 8080
CMD [ "npm", "start" ]