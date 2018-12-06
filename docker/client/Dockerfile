FROM node:8 as builder

WORKDIR /usr/src/app
ADD client /usr/src/app

RUN npm config set registry http://172.16.0.28:8081/repository/npm-proxy/ && \
    npm install && \
    npm run build

FROM nginx:1.15

COPY --from=builder /usr/src/app/dist /opt/web
ADD docker/client/app-publisher.conf /etc/nginx/conf.d/default.conf
# ADD docker/nginx.conf /etc/nginx/nginx.conf

RUN mkdir /opt/logs