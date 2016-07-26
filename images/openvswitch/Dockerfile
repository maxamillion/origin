#
# This is an openvswitch image meant to enable OpenShift OVS based SDN
#
# The standard name for this image is openshift/openvswitch
#
FROM maxamillion/origin-base

MAINTAINER Scott Dodson <sdodson@redhat.com>

RUN INSTALL_PKGS="openvswitch" && \
    dnf install -y $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    dnf clean all

ADD  scripts/* /usr/local/bin/
RUN chmod +x /usr/local/bin/*
VOLUME [ "/etc/openswitch" ]

ENV HOME /root
ENTRYPOINT [ "/usr/local/bin/ovs-run.sh" ]
