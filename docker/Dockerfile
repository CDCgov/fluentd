FROM fluent/fluentd:v0.12.40

MAINTAINER Tim Taylor <ttaylor@mitre.org>
LABEL maintainer "Tim Taylor <ttaylor@mitre.org>"

USER 0

# Replace the original entrypoint script with ours
COPY entrypoint.sh /bin/

# Make the fluent directories owned by root group and group writable
RUN    adduser -D -g '' -u 1001 -h /home/fluent fluent \
    && chgrp -R root /home/fluent \
    && chgrp -R root /fluentd \
    && chmod -R g+rw /home/fluent \
    && chmod -R g+rw /fluentd \
    && chmod +x /bin/entrypoint.sh

VOLUME /fluentd/log

USER 1001
