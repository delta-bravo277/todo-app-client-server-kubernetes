FROM node:14-alpine as todo-app-build

WORKDIR /client

COPY package.json yarn.lock README.md ./

RUN yarn

COPY ./public ./public

COPY ./src ./src

ENV REACT_APP_baseAPIURL=http://43.205.145.39:5000

RUN yarn build

FROM nginx:latest

COPY --from=todo-app-build /client/build/ /usr/share/nginx/html

EXPOSE 80
