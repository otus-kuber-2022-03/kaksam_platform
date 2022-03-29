FROM nginx
COPY default.conf /etc/nginx/conf.d/default.conf
ADD app /app
WORKDIR /app
RUN usermod -u 1001 nginx \
  && groupmod -g 1001 nginx
RUN chown -R nginx:nginx /app
EXPOSE 8000
CMD ["nginx", "-g", "daemon off;"]