ARG NGINX_VERSION
#基于 nginx:1.19.1-alpine镜像
FROM ${NGINX_VERSION}
ARG TZ
ARG NGINX_VERSION
ARG CONTAINER_PACKAGE_URL
ARG NGINX_INSTALL_APPS
ENV INSTALL_APPS=",${NGINX_INSTALL_APPS},"
RUN if [ "${CONTAINER_PACKAGE_URL}" != "" ]; then \
        sed -i "s/dl-cdn.alpinelinux.org/${CONTAINER_PACKAGE_URL}/g" /etc/apk/repositories; \
    fi
RUN if [ -z "${INSTALL_APPS##*,certbot,*}" ]; then \
        echo "---------- Install certbot ----------"; \
        apk add --no-cache certbot; \
    fi
#进入容器(e.g.docker exec -it xxx sh)后所在的目录
WORKDIR /www
