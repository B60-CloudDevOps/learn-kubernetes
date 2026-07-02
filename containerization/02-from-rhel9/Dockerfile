FROM        docker.io/redhat/ubi9:9.8-source
RUN         dnf install -y nginx && \
            dnf clean all && \
            rm -rf /var/cache/dnf 
RUN         rm -rf /usr/share/nginx/html/*
COPY        index.html /usr/share/nginx/html/index.html 
ENTRYPOINT  ["nginx", "-g", "daemon off;"]
EXPOSE      80