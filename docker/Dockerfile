FROM python:2.7-alpine

RUN true \
    && apk update \
    && apk --no-cache add ca-certificates tini gcc g++ musl-dev curl \
    && rm -rf "/tmp/*" "/root/.cache" `find / -regex '.*\.py[co]'`

RUN true \
    && pip install locustio==0.8.1 pyzmq \
    && mkdir /locust

WORKDIR /locust

ADD tasks/* /locust/
RUN test -f requirements.txt && pip install -r requirements.txt; exit 0

EXPOSE 5557 5558 8089

# Start Locust using LOCUS_OPTS environment variable
ENTRYPOINT ["/sbin/tini", "--"]
CMD ["/locust/run.sh"]
