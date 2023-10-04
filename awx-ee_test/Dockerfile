FROM quay.io/alice_golakiya/awx-operator:1.0.0
USER root

# RUN sed -i 's/\(def in_container():\)/\1\n    return False/g' /usr/lib64/python*/*-packages/rhsm/config.py
# RUN  subscription-manager register --username rajeshtanuku --password India@12031984 --auto-attach
# RUN subscription-manager refresh
ARG PKGMGR
ARG ANSIBLE_INSTALL_REFS
ARG ANSIBLE_GALAXY_CLI_ROLE_OPTS
ARG ANSIBLE_GALAXY_CLI_COLLECTION_OPTS
ARG PKGMGR_PRESERVE_CACHE
ARG PYCMD
ARG EE_BASE_IMAGE

# RUN |7 EE_BASE_IMAGE=quay.io/centos/centos:stream9 PYCMD=/usr/bin/python3 PKGMGR_PRESERVE_CACHE= ANSIBLE_GALAXY_CLI_COLLECTION_OPTS= ANSIBLE_GALAXY_CLI_ROLE_OPTS= ANSIBLE_INSTALL_REFS=ansible-core>=2.15.0rc2,<2.16 ansible-runner PKGMGR=/usr/bin/dnf /bin/sh -c $PYCMD -m ensurepip # buildkit
RUN python3 -m ensurepip
RUN python3 -m pip install --no-cache-dir ansible-core>=2.15

# RUN mkdir /opt/builder && mkdir -p /opt/ansible/output/scripts
COPY scripts/entrypoint /opt/builder/bin/entrypoint
COPY scripts/check_ansible /opt/ansible/check_ansible

RUN python3 -m pip install -U pip

ARG PKGMGR
ARG ANSIBLE_INSTALL_REFS
ARG ANSIBLE_GALAXY_CLI_ROLE_OPTS
ARG ANSIBLE_GALAXY_CLI_COLLECTION_OPTS
ARG PKGMGR_PRESERVE_CACHE
ARG PYCMD
ARG EE_BASE_IMAGE
