file:57403e8900877fcdb89d96ad31428d0a92643d6c250869e5d42f8201f1d434ea in /
# org.label-schema.schema-version="1.0" org.label-schema.name="CentOS Stream 9 Base Image" org.label-schema.vendor="CentOS" org.label-schema.license="GPLv2" org.label-schema.build-date="20231002"
CMD ["/bin/bash"]
USER root
ARG PKGMGR
ARG ANSIBLE_INSTALL_REFS
ARG ANSIBLE_GALAXY_CLI_ROLE_OPTS
ARG ANSIBLE_GALAXY_CLI_COLLECTION_OPTS
ARG PKGMGR_PRESERVE_CACHE
ARG PYCMD
ARG EE_BASE_IMAGE

RUN |7 EE_BASE_IMAGE=quay.io/centos/centos:stream9 PYCMD=/usr/bin/python3 PKGMGR_PRESERVE_CACHE= ANSIBLE_GALAXY_CLI_COLLECTION_OPTS= ANSIBLE_GALAXY_CLI_ROLE_OPTS= ANSIBLE_INSTALL_REFS=ansible-core>=2.15.0rc2,<2.16 ansible-runner PKGMGR=/usr/bin/dnf /bin/sh -c $PYCMD -m ensurepip # buildkit
RUN |7 EE_BASE_IMAGE=quay.io/centos/centos:stream9 PYCMD=/usr/bin/python3 PKGMGR_PRESERVE_CACHE= ANSIBLE_GALAXY_CLI_COLLECTION_OPTS= ANSIBLE_GALAXY_CLI_ROLE_OPTS= ANSIBLE_INSTALL_REFS=ansible-core>=2.15.0rc2,<2.16 ansible-runner PKGMGR=/usr/bin/dnf /bin/sh -c $PYCMD -m pip install --no-cache-dir $ANSIBLE_INSTALL_REFS # buildkit

COPY _build/scripts/entrypoint /opt/builder/bin/entrypoint # buildkit
COPY _build/scripts/ /output/scripts/ # buildkit

RUN |7 EE_BASE_IMAGE=quay.io/centos/centos:stream9 PYCMD=/usr/bin/python3 PKGMGR_PRESERVE_CACHE= ANSIBLE_GALAXY_CLI_COLLECTION_OPTS= ANSIBLE_GALAXY_CLI_ROLE_OPTS= ANSIBLE_INSTALL_REFS=ansible-core>=2.15.0rc2,<2.16 ansible-runner PKGMGR=/usr/bin/dnf /bin/sh -c $PYCMD -m pip install -U pip # buildkit

ARG PKGMGR
ARG ANSIBLE_INSTALL_REFS
ARG ANSIBLE_GALAXY_CLI_ROLE_OPTS
ARG ANSIBLE_GALAXY_CLI_COLLECTION_OPTS
ARG PKGMGR_PRESERVE_CACHE
ARG PYCMD
ARG EE_BASE_IMAGE

RUN |7 EE_BASE_IMAGE=quay.io/centos/centos:stream9 PYCMD=/usr/bin/python3 PKGMGR_PRESERVE_CACHE= ANSIBLE_GALAXY_CLI_COLLECTION_OPTS= ANSIBLE_GALAXY_CLI_ROLE_OPTS= ANSIBLE_INSTALL_REFS=ansible-core>=2.15.0rc2,<2.16 ansible-runner PKGMGR=/usr/bin/dnf /bin/sh -c /output/scripts/check_ansible $PYCMD # buildkit

COPY /output/ /output/ # buildkit
COPY /usr/share/ansible /usr/share/ansible # buildkit

RUN |7 EE_BASE_IMAGE=quay.io/centos/centos:stream9 PYCMD=/usr/bin/python3 PKGMGR_PRESERVE_CACHE= ANSIBLE_GALAXY_CLI_COLLECTION_OPTS= ANSIBLE_GALAXY_CLI_ROLE_OPTS= ANSIBLE_INSTALL_REFS=ansible-core>=2.15.0rc2,<2.16 ansible-runner PKGMGR=/usr/bin/dnf /bin/sh -c /output/scripts/install-from-bindep 
# && rm -rf /output/wheels # buildkit

RUN |7 EE_BASE_IMAGE=quay.io/centos/centos:stream9 PYCMD=/usr/bin/python3 PKGMGR_PRESERVE_CACHE= ANSIBLE_GALAXY_CLI_COLLECTION_OPTS= ANSIBLE_GALAXY_CLI_ROLE_OPTS= ANSIBLE_INSTALL_REFS=ansible-core>=2.15.0rc2,<2.16 ansible-runner PKGMGR=/usr/bin/dnf /bin/sh -c chmod ug+rw /etc/passwd # buildkit

RUN |7 EE_BASE_IMAGE=quay.io/centos/centos:stream9 PYCMD=/usr/bin/python3 PKGMGR_PRESERVE_CACHE= ANSIBLE_GALAXY_CLI_COLLECTION_OPTS= ANSIBLE_GALAXY_CLI_ROLE_OPTS= ANSIBLE_INSTALL_REFS=ansible-core>=2.15.0rc2,<2.16 ansible-runner PKGMGR=/usr/bin/dnf /bin/sh -c mkdir -p /runner && chgrp 0 /runner && chmod -R ug+rwx /runner # buildkit


WORKDIR /runner

RUN |7 EE_BASE_IMAGE=quay.io/centos/centos:stream9 PYCMD=/usr/bin/python3 PKGMGR_PRESERVE_CACHE= ANSIBLE_GALAXY_CLI_COLLECTION_OPTS= ANSIBLE_GALAXY_CLI_ROLE_OPTS= ANSIBLE_INSTALL_REFS=ansible-core>=2.15.0rc2,<2.16 ansible-runner PKGMGR=/usr/bin/dnf /bin/sh -c $PYCMD -m pip install --no-cache-dir 'dumb-init==1.2.5' # buildkit

COPY /usr/bin/receptor /usr/bin/receptor # buildkit

RUN |7 EE_BASE_IMAGE=quay.io/centos/centos:stream9 PYCMD=/usr/bin/python3 PKGMGR_PRESERVE_CACHE= ANSIBLE_GALAXY_CLI_COLLECTION_OPTS= ANSIBLE_GALAXY_CLI_ROLE_OPTS= ANSIBLE_INSTALL_REFS=ansible-core>=2.15.0rc2,<2.16 ansible-runner PKGMGR=/usr/bin/dnf /bin/sh -c mkdir -p /var/run/receptor # buildkit
RUN |7 EE_BASE_IMAGE=quay.io/centos/centos:stream9 PYCMD=/usr/bin/python3 PKGMGR_PRESERVE_CACHE= ANSIBLE_GALAXY_CLI_COLLECTION_OPTS= ANSIBLE_GALAXY_CLI_ROLE_OPTS= ANSIBLE_INSTALL_REFS=ansible-core>=2.15.0rc2,<2.16 ansible-runner PKGMGR=/usr/bin/dnf /bin/sh -c git lfs install --system # buildkit
# RUN |7 EE_BASE_IMAGE=quay.io/centos/centos:stream9 PYCMD=/usr/bin/python3 PKGMGR_PRESERVE_CACHE= ANSIBLE_GALAXY_CLI_COLLECTION_OPTS= ANSIBLE_GALAXY_CLI_ROLE_OPTS= ANSIBLE_INSTALL_REFS=ansible-core>=2.15.0rc2,<2.16 ansible-runner PKGMGR=/usr/bin/dnf /bin/sh -c rm -rf /output # buildkit

LABEL ansible-execution-environment=true
USER 1000
ENTRYPOINT ["/opt/builder/bin/entrypoint" "dumb-init"]
CMD ["bash"]
