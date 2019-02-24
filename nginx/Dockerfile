FROM nginx:stable-alpine
COPY site.conf /etc/nginx/conf.d/default.conf
WORKDIR /app
COPY site/index.php .
EXPOSE 80
