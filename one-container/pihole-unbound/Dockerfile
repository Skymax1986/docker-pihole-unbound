ARG PIHOLE_VERSION
FROM pihole/pihole:${PIHOLE_VERSION:-latest}
RUN apt update && apt install -y unbound

COPY lighttpd-external.conf /etc/lighttpd/external.conf 
RUN echo "include: \"/opt/unbound/*.conf\"" >> /etc/unbound/unbound.conf 
COPY 99-edns.conf /etc/dnsmasq.d/99-edns.conf
RUN mkdir -p /etc/services.d/unbound
COPY unbound-run /etc/services.d/unbound/run

ENTRYPOINT ./s6-init

