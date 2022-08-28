FROM alpine:latest

RUN apk add --no-cache tzdata ca-certificates supervisor inotify-tools \
    && mkdir -p /var/log/xray /usr/share/xray \
    && wget -O /usr/bin/xray https://dl.lamp.sh/files/xray_linux_amd64 \
    && wget -O /usr/share/xray/geosite.dat https://github.com/v2fly/domain-list-community/releases/latest/download/dlc.dat \
    && wget -O /usr/share/xray/geoip.dat https://github.com/v2fly/geoip/releases/latest/download/geoip.dat \
    && chmod +x /usr/bin/xray

COPY supervisord.conf /etc/supervisord.conf

ENV TZ=Asia/Jakarta

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisord.conf"]