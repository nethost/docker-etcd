FROM nethost/alpine:3.6
MAINTAINER billgo <cocobill@vip.qq.com>

RUN apk --no-cache add curl wget jq bind-tools
ENV ETCD_VERSION 3.2.9
RUN curl -L https://github.com/coreos/etcd/releases/download/v${ETCD_VERSION}/etcd-v${ETCD_VERSION}-linux-amd64.tar.gz -o etcd.tar.gz && \
    tar xzf etcd.tar.gz && \
    mv etcd-*/etcd /etcd-*/etcdctl /bin/ && \
    /bin/etcd --version && \
    rm -rf etcd.tar.gz etcd-*

COPY entrypoint.sh /bin/
RUN chmod +x /bin/entrypoint.sh

VOLUME /data

EXPOSE 2379 2380 4001 7001

ENV MIN_SEEDS_COUNT 2
ENV ETCDCTL_API=3

ENTRYPOINT ["/bin/entrypoint.sh"]