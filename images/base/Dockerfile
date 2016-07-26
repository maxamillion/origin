#
# This is the base image from which all OpenShift Origin images inherit. Only packages
# common to all downstream images should be here. Depends on Fedora 24+
#
# The standard name for this image is openshift/origin-base
#
FROM fedora:24

RUN dnf update -y --refresh --allowerasing && \
    dnf clean all

RUN INSTALL_PKGS="which git tar wget hostname util-linux bsdtar \
      socat ethtool device-mapper iptables tree findutils nmap-ncat \
      e2fsprogs xfsprogs lsof" && \
    dnf install -y $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    dnf clean all && \
    mkdir -p /var/lib/origin

LABEL io.k8s.display-name="OpenShift Origin Fedora 24 Base" \
      io.k8s.description="This is the base image from which all OpenShift Origin images inherit."
