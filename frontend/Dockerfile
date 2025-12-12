#FROM nginx
#FROM nginx:stable-alpine3.20-perl
#RUN rm -rf /usr/share/nginx/html/index.html
##RUN rm -rf /etc/nginx/nginx.conf
##RUN rm -rf /etc/nginx/conf.d/default.conf
#COPY nginx.conf /etc/nginx/nginx.conf
#RUN mkdir -p /var/cache/nginx/client_temp && \
#        mkdir -p /var/cache/nginx/proxy_temp && \
#        mkdir -p /var/cache/nginx/fastcgi_temp && \
#        mkdir -p /var/cache/nginx/uwsgi_temp && \
#        mkdir -p /var/cache/nginx/scgi_temp && \
#        chown -R nginx:nginx /var/cache/nginx && \
#        chown -R nginx:nginx /etc/nginx/ && \
#        chmod -R 755 /etc/nginx/ && \
#        chown -R nginx:nginx /var/log/nginx

#RUN mkdir -p /etc/nginx/ssl/ && \
#    chown -R nginx:nginx /etc/nginx/ssl/ && \
#    chmod -R 755 /etc/nginx/ssl/

#RUN touch /var/run/nginx.pid && \
#    chown -R nginx:nginx /var/run/nginx.pid /run/nginx.pid
#COPY nginx.conf /etc/nginx/nginx.conf
#COPY code /usr/share/nginx/html/
#USER nginx

FROM nginx:stable-alpine3.20-perl

# Remove default configs
RUN rm -rf /etc/nginx/nginx.conf \
           /etc/nginx/conf.d/default.conf \
           /usr/share/nginx/html/*

# Copy your custom nginx config
COPY nginx.conf /etc/nginx/nginx.conf

# Copy frontend build output
COPY code /usr/share/nginx/html/

# Permissions (nginx user still exists)
RUN chown -R nginx:nginx /usr/share/nginx/html

# Expose HTTP port
EXPOSE 80

# Start NGINX
CMD ["nginx", "-g", "daemon off;"]
