FROM redis:4-alpine AS redis

RUN echo "never > /sys/kernel/mm/transparent_hugepage/enabled" >> /etc/rc.local \
&& echo "sysctl -w net.core.somaxconn=65535" >> /etc/rc.local

COPY redis.conf /usr/local/etc/redis/redis.conf
CMD [ "redis-server", "/usr/local/etc/redis/redis.conf" ]