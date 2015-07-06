#
# This is the base image from which all OpenShift Origin images inherit. Only packages
# common to all downstream images should be here.
#
# The standard name for this image is openshift/origin-base
#
FROM maxamillion/fedora-armhfp

# components from EPEL must be installed in a separate yum install step
RUN dnf -y update && \
    dnf install -y git tar wget socat hostname sysvinit-tools util-linux && \
    dnf clean all
