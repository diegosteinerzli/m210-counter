FROM node:17.5.0-alpine3.14

ENV APP_ROOT=/srv/app
ENV USER_NAME=app
ENV USER_UID=1001
ENV HOME=/opt/${USER_NAME}

COPY [ "./bin",  "/usr/local/bin/"]
COPY [ "package.json", "package-lock.json",  "${APP_ROOT}/"]
COPY [ "config", "${APP_ROOT}/config"]
COPY [ "src", "${APP_ROOT}/src"]

USER 0

RUN /usr/local/bin/user_setup

USER ${USER_UID}

WORKDIR ${APP_ROOT}

RUN npm install; \
    npm run build

EXPOSE 8080
ENTRYPOINT [ "/usr/local/bin/entrypoint" ]
CMD [ "npm", "start" ]