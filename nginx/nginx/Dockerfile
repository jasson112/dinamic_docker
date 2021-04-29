FROM nginx:alpine

COPY conf /etc/nginx/conf.d
COPY nginx.conf /etc/nginx/nginx.conf

RUN mkdir -p /etc/nginx/sites-enabled
RUN mkdir -p /etc/nginx/sites-available