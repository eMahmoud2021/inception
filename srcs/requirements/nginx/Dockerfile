FROM debian:buster

RUN	apt-get update && \
    apt-get install -y nginx openssl


RUN		openssl req -new -newkey rsa:4096 -x509 -sha512 -days 365 -nodes \
		-subj "/C=FR/ST=Alsace/L=Mulhouse/O=42/OU=42_Mulhouse/CN=memam.42.fr/USERID=memam"\
		-out /etc/ssl/certs/nginx_certificate.crt  \
		-keyout /etc/ssl/private/nginx_certificate.key


COPY	./conf/nginx.conf	/etc/nginx/conf.d

EXPOSE	443

RUN ln -sf /dev/stdout /var/log/nginx/access.log && \
    ln -sf /dev/stderr /var/log/nginx/error.log

CMD  ["nginx", "-g", "daemon off;"]
