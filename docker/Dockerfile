FROM nginx:1.25-alpine

COPY app/index.html /usr/share/nginx/html/index.html

HEALTHCHECK --interval=30s --timeout=5s \ 
CMD wget -qO- http://localhost || exit 1
