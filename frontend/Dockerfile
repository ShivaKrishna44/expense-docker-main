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

FROM nginx:stable-alpine
# Remove default config
RUN rm -rf /etc/nginx/conf.d/default.conf
# Copy custom config
COPY nginx.conf /etc/nginx/nginx.conf
# Copy built frontend files
COPY code /usr/share/nginx/html/
# Use non-root user for security
#USER nginx
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
