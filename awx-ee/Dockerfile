FROM quay.io/ansible/awx-ee:latest
USER root

RUN dnf install subscription-manager -y

# RUN sed -i 's/\(def in_container():\)/\1\n    return False/g' /usr/lib64/python*/*-packages/rhsm/config.py
RUN  subscription-manager register --username rajeshtanuku --password India@12031984 --auto-attach
RUN subscription-manager refresh

RUN  yum update xz-libs -y
RUN yum update subversion -y
RUN yum update subversion-libs -y
RUN yum update python3 -y
RUN yum update python3-libs -y
RUN yum update python-unversioned-command -y
RUN yum update libksba -y
RUN yum update git-core -y
RUN yum update vim-minimal -y
