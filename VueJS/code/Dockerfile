FROM node:10 AS builder

WORKDIR /var/www

COPY src .

RUN npm install

RUN npm run build

CMD ["node"]

FROM nginx:1.17

WORKDIR /var/www

COPY --from=builder /var/www/dist /var/www/dist

COPY nginx/vhost /etc/nginx/conf.d/default.conf

CMD [ "nginx","-g","daemon off;" ]