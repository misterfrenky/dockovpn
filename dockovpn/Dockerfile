FROM alpine:3.14.1

LABEL maintainer="Alexander Litvinenko <array.shift@yahoo.com>"

# System settings. User normally shouldn't change these parameters
ENV APP_NAME Dockovpn
ENV APP_INSTALL_PATH /opt/${APP_NAME}
ENV APP_PERSIST_DIR /opt/${APP_NAME}_data

# Configuration settings with default values
ARG HOST_ADDR
ARG HOST_TUN_PORT
ARG HOST_CONF_PORT
ARG HOST_TUN_PROTOCOL


ENV NET_ADAPTER eth0
ENV HOST_ADDR=$HOST_ADDR
ENV HOST_TUN_PORT=$HOST_TUN_PORT
ENV HOST_CONF_PORT=$HOST_CONF_PORT
ENV HOST_TUN_PROTOCOL=$HOST_TUN_PROTOCOL
ENV CRL_DAYS 3650

WORKDIR ${APP_INSTALL_PATH}

COPY scripts .
COPY config ./config
COPY VERSION ./config

RUN apk add --no-cache openvpn easy-rsa bash netcat-openbsd zip curl dumb-init && \
    ln -s /usr/share/easy-rsa/easyrsa /usr/bin/easyrsa && \
    mkdir -p ${APP_PERSIST_DIR} && \
    cd ${APP_PERSIST_DIR} && \
    easyrsa init-pki && \
    easyrsa gen-dh && \
    # DH parameters of size 2048 created at /usr/share/easy-rsa/pki/dh.pem
    # Copy DH file
    cp pki/dh.pem /etc/openvpn && \
    # Copy FROM ./scripts/server/conf TO /etc/openvpn/server.conf in DockerFile
    cd ${APP_INSTALL_PATH} && \
    cp config/server.conf /etc/openvpn/server.conf


EXPOSE 1194/${HOST_TUN_PROTOCOL}
EXPOSE 8080/tcp

VOLUME [ "/opt/Dockovpn_data" ]

ENTRYPOINT [ "dumb-init", "./start.sh" ]
CMD [ "" ]
