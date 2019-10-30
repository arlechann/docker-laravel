FROM nginx:latest

RUN mkdir -p /var/www/public && \
	chown -R nginx:nginx /var/www && \
	mv /usr/share/nginx/html/* /var/www/public

COPY default.conf /etc/nginx/conf.d

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
