FROM alpine:3.3

RUN apk add --no-cache openssl python

RUN wget https://bootstrap.pypa.io/get-pip.py \
    && python get-pip.py

RUN pip install -i http://pypi.douban.com/simple/ supervisor \
    && echo_supervisord_conf > /etc/supervisord.conf

RUN mkdir -p /etc/supervisor.d \
    && sed -i "s/;nodaemon=false/nodaemon=true/g" /etc/supervisord.conf \
    && sed -i "s/;\[include\]/\[include\]/g" /etc/supervisord.conf \
    && sed -i "s/;files\s*=\s*relative\/directory\/\*.ini/files=\/etc\/supervisor.d\/\*.conf/g" /etc/supervisord.conf

CMD ["supervisord", "-n", "-c", "/etc/supervisord.conf"]
