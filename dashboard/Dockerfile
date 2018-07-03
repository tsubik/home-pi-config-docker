# RUN mkdir /var/deploy

# WORKDIR /var/deploy

# COPY Caddyfile /etc/Caddyfile
# CMD ["--conf", "/etc/Caddyfile", "--log", "stdout", "--agree", "--ca", "https://acme-staging.api.letsencrypt.org/directory"]


FROM armhf/alpine:latest
MAINTAINER Adriel Kloppenburg

LABEL caddy_version="0.11.0" architecture="armhf"

RUN apk add --no-cache tar curl git

ARG plugins=http.filemanager,http.reauth

RUN curl --show-error --fail --location \
"https://caddyserver.com/download/linux/arm7?plugins=${plugins}&license=personal&telemetry=off" \
| tar --no-same-owner -C /usr/bin/ -xz caddy \
&& chmod 0755 /usr/bin/caddy \
&& /usr/bin/caddy -version

EXPOSE 80 443 2015
VOLUME /root/.caddy
WORKDIR /srv

COPY Caddyfile /etc/Caddyfile
# COPY index.html /srv/index.html

RUN /usr/bin/caddy -validate --conf /etc/Caddyfile

ENTRYPOINT ["/usr/bin/caddy"]
CMD ["--conf", "/etc/Caddyfile", "--log", "stdout"]
