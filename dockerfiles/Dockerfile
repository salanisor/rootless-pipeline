#
# Dockerfile template for Tuxedo 12.1.3
# 
# Download the following files to an empty directory:
#   tuxedo121300_64_Linux_01_x86.zip http://www.oracle.com/technetwork/middleware/tuxedo/downloads/index.html
#   p22090512_121300_Linux-x86-64.zip 	or whatever the latest Tuxedo rolling patch is from My Oracle Support
#

# Pull base image
# FROM docker.io/store/oracle/serverjre:1.8.0_241-b07
# FROM https://registry.access.redhat.com/openjdk/openjdk-11-rhel7:1.10-1.1634744381
FROM quay.io/canit0/serverjre:1.8.0_241-b07

MAINTAINER Judy Liu <judy.liu@oracle.com>

# Common environment variables required for this build (do NOT change)
# --------------------------------------------------------------------
ENV ORACLE_HOME=/u01/oracle \
    PATH=/usr/java/default/bin:$PATH \
    TUX_PKG=tuxedo121300_64_Linux_01_x86.zip

# Core install doesn't include unzip or gcc, add them
# Setup filesystem and oracle user
# Adjust file permissions, go to /u01 as user 'oracle' to proceed with WLS installation
# ------------------------------------------------------------
RUN yum -y install unzip gcc file hostname which util-linux && rm -rf /var/cache/yum && \
    mkdir -p /u01 && chmod a+xr /u01 && \
    groupadd -g 1000 oracle && useradd -b /u01 -m -g oracle -u 1000 -s /bin/bash oracle 

# Copy packages
# -------------
RUN  chown oracle:oracle -R /u01

USER oracle
WORKDIR /u01/oracle
