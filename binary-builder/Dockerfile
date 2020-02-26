# basic-binary
FROM registry.access.redhat.com/rhel7/rhel-atomic

LABEL io.k8s.description="Platform for building basic binaries" \
      io.k8s.display-name="builder base" \
      io.openshift.s2i.scripts-url="image:///usr/libexec/s2i"

COPY ./s2i/bin/ /usr/libexec/s2i

WORKDIR /opt/app-root/src/

ENV USER_UID=1001

RUN chown -R ${USER_UID}:${USER_UID} /opt/app-root

ENV PATH="/opt/app-root/src:${PATH}"

COPY ./bin /usr/local/bin

RUN  /usr/local/bin/user_setup

USER ${USER_UID}
