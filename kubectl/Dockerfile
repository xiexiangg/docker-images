FROM alpine:3.8

MAINTAINER xiexiang <xiexiang168@gmail.com>

ARG ARCH="amd64"
ARG KUBE_VERSION="v1.24.3"

RUN apk add --update ca-certificates \
&& apk add --update -t deps curl \
 && apk add --update gettext \
 && apk add --update git \
 && curl -L --remote-name-all https://storage.googleapis.com/kubernetes-release/release/${RELEASE}/bin/linux/${ARCH}/kubectl -o /usr/local/bin/kubectl \
 && chmod +x /usr/local/bin/kubectl \
 && apk del --purge deps \
 && rm /var/cache/apk/*

ENTRYPOINT ["kubectl"]
CMD ["--help"]