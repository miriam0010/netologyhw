FROM nginx:1.21.1

RUN rm /usr/share/nginx/html/index.html

COPY index.html /usr/share/nginx/html/

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
