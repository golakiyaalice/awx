#FROM quay.io/alice_golakiya/awx-operator:critical_high_fix
FROM registry.access.redhat.com/ubi8/ubi
CMD ["/bin/bash"]
USER root
RUN sed -i 's/\(def in_container():\)/\1\n    return False/g' /usr/lib64/python*/*-packages/rhsm/config.py
RUN  subscription-manager register --username rajeshtanuku --password India@12031984 --auto-attach
RUN dnf update -y
RUN yum install python3.9 -y
RUN python3 -m ensurepip
RUN python3 -m pip install -U pip

# RUN python3 -m pip install --no-cache-dir ansible-core>=2.15
RUN python3 -m pip install ansible 
RUN pip install ansible-builder

COPY files/requirements.yml ./
RUN ansible-galaxy collection install -r ./requirements.yml --collections-path /usr/share/ansible/collections

COPY scripts/entrypoint /opt/builder/bin/entrypoint
COPY scripts/check_ansible /output/scripts/check_ansible

CMD /output/scripts/check_ansible /usr/bin/python3

COPY scripts/install-from-bindep /output/scripts/install-from-bindep
CMD /output/scripts/install-from-bindep && rm -rf /output/wheels
CMD chmod ug+rw /etc/passwd
RUN mkdir -p /runner && chgrp 0 /runner && chmod -R ug+rwx /runner

WORKDIR /runner

RUN python3 -m pip install --no-cache-dir 'dumb-init==1.2.5'

COPY scripts/receptor /usr/bin/receptor
RUN mkdir -p /var/run/receptor
CMD git lfs install --system
CMD rm -rf /output

#Remediation steps below
#RUN yum install xz-libs -y
RUN yum install python38-devel -y
RUN pip install svn
#RUN yum install svn-libs -y
#RUN yum install python3 -y
RUN yum install python3-libs -y
#RUN pip install python-unversioned-command
RUN yum install libksba -y
RUN yum install git-core -y
RUN yum install vim-minimal -y
RUN pip install certifi==2023.7.22
#Remediation steps complete

#USER 1000
#CMD chmod a+x /opt/builder/bin/entrypoint
#ENTRYPOINT  ["/opt/builder/bin/entrypoint" "dumb-init"]
CMD ["bash"]
