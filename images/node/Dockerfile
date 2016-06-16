#
# This is an OpenShift Origin node image with integrated OpenvSwitch SDN
# If you do not require OVS SDN use the maxamillion/origin image instead.
#
# This image expects to have a volume mounted at /etc/origin/node that contains
# a KUBECONFIG file giving the node permission to talk to the master and a
# node configuration file.
#
# The standard name for this image is maxamillion/node
#

FROM maxamillion/origin

# Based on work by: Peter Schiffer <pschiffe@redhat.com>
MAINTAINER Devan Goodwin <dgoodwin@redhat.com>

<<<<<<< HEAD
# We need to install openvswitch for the client portions, the daemons are expected
# to run in another container

RUN curl -L -o /etc/yum.repos.d/maxamillion-fedora-origin-24.repo https://copr.fedorainfracloud.org/coprs/maxamillion/fedora-openshift/repo/fedora-24/maxamillion-fedora-openshift-fedora-24.repo && \
    INSTALL_PKGS="libmnl libnetfilter_conntrack openvswitch libnfnetlink iptables iproute bridge-utils procps-ng ethtool socat openssl binutils xz kmod-libs kmod sysvinit-tools device-mapper-libs dbus ceph-common iscsi-initiator-utils" && \
    dnf install -y $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    dnf clean all

RUN mkdir -p \
    /usr/lib/systemd/system/origin-node.service.d \
    /usr/lib/systemd/system/docker.service.d

# All of the following are placed in images/node by hack/build-images.sh
# They won't exist in the git checkout
ADD bin/* /usr/bin/
ADD conf/openshift-sdn-ovs.conf /usr/lib/systemd/system/origin-node.service.d/
ADD lib/systemd/system/docker.service.d/docker-sdn-ovs.conf /usr/lib/systemd/system/docker.service.d/docker-sdn-ovs.conf
ADD scripts/* /usr/local/bin/
RUN chmod +x /usr/local/bin/* /usr/bin/openshift-*

VOLUME [ "/etc/origin/node", "/var/lib/origin" ]
WORKDIR /var/lib/origin

ENV HOME /root
ENV OPENSHIFT_CONTAINERIZED true
ENV KUBECONFIG /etc/origin/node/node.kubeconfig
ENTRYPOINT []
CMD [ "/usr/local/bin/origin-node-run.sh" ]
