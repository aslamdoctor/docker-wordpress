FROM nginx:stable-alpine

RUN apk --update --no-cache add openssl

RUN mkdir -p /etc/nginx/certs/ /etc/nginx/certs/private/

RUN openssl req -x509 -nodes -days 365 -subj "/C=CA/ST=QC/O=Tplus, Inc./CN=localhost" \
    -addext "subjectAltName=DNS:localhost" -newkey rsa:2048 \
    -keyout /etc/nginx/certs/private/self-signed.key \
    -out /etc/nginx/certs/self-signed.crt;
