ARG JITSI_REPO=jitsi
FROM ${JITSI_REPO}/base

ARG JITSI_MEET_VERSION
RUN \
	apt-dpkg-wrap apt-get update && \
	apt-dpkg-wrap apt-get install -y cron nginx-extras jitsi-meet-web=1.0.${JITSI_MEET_VERSION}* && \
	apt-dpkg-wrap apt-get install -y -t stretch-backports certbot && \
	apt-cleanup && \
	rm -f /etc/nginx/conf.d/default.conf && \
	mkdir /defaults && \
	mv /usr/share/jitsi-meet/interface_config.js /defaults/interface_config.js

COPY rootfs/ /

EXPOSE 80 443

VOLUME ["/config", "/etc/letsencrypt"]
