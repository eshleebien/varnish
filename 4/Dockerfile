FROM wodby/alpine:3.6-1.2.0

ARG VARNISH_VER
ARG VARNISH_VER_ALPINE

ENV VARNISH_VER="${VARNISH_VER}"

RUN apk --update --no-cache -t .varnish-rundeps add \
        make \
        pwgen \
        varnish="${VARNISH_VER_ALPINE}"; \
    \
    # We don't use default init
    echo "" > /etc/init.d/varnishd

EXPOSE 6081 6082

VOLUME /var/lib/varnish

COPY templates /etc/gotpl/
COPY templates/default_custom.vcl /etc/varnish/custom.vcl
COPY actions /usr/local/bin/
COPY docker-entrypoint.sh /

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["/etc/init.d/varnishd"]
