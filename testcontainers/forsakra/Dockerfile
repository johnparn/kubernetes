FROM nginx:1.13-alpine

# Site content
COPY ./build/ /usr/share/nginx/html/

# Nginx conf
#COPY docker/nginx/nginx.conf /etc/nginx/nginx.conf
#COPY docker/nginx/conf.d /etc/nginx/conf.d

# forward request logs to Docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
    && ln -sf /dev/stderr /var/log/nginx/error.log

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
