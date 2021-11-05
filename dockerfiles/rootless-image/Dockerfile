ARG SOURCE_IMAGE=quay.io/buildah/stable:v1.23.0
FROM $SOURCE_IMAGE

ARG OC_URL=http://downloads.openshift-console.svc/amd64/linux/oc.tar

RUN yum install -y make findutils git && \
    curl -fsSL ${OC_URL} -o /tmp/oc.tar && \
    mkdir -p /tmp/octar && \
    tar -xvf /tmp/oc.tar -C /tmp/octar && \
    mv /tmp/octar/oc /usr/local/bin/ && \
    chmod a+x /usr/local/bin/oc && \
    rm -rf /tmp/oc* && \
    yum clean all && \
    rm -rf /var/cache/yum

COPY resources/ usr/local/bin/
