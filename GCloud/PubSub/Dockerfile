FROM google/cloud-sdk:alpine

RUN apk --update --no-cache add ca-certificates openjdk7-jre \
    && rm -rf /var/cache/apk/*

RUN gcloud components install --quiet beta pubsub-emulator \
    && gcloud components update

RUN mkdir -p /var/pubsub

VOLUME /var/pubsub

EXPOSE 8085

CMD ["gcloud", "beta", "emulators", "pubsub", "start", "--data-dir=/var/pubsub", "--host-port=0.0.0.0:8085", "--log-http", "--verbosity=debug", "--user-output-enabled"]