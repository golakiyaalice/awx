FROM quay.io/alice_golakiya/awx-operator:critical_high_fix
CMD ["/bin/bash"]
USER root

RUN python3 -m ensurepip
RUN python3 -m pip install --no-cache-dir ansible-core>=2.15

COPY scripts/entrypoint /opt/builder/bin/entrypoint
COPY scripts/check_ansible /output/scripts/check_ansible

RUN python3 -m pip install -U pip

CMD /output/scripts/check_ansible /usr/bin/python3

COPY scripts/install-from-bindep /output/scripts/install-from-bindep
CMD /output/scripts/install-from-bindep
CMD chmod ug+rw /etc/passwd
RUN mkdir -p /runner && chgrp 0 /runner && chmod -R ug+rwx /runner

WORKDIR /runner

RUN python3 -m pip install --no-cache-dir 'dumb-init==1.2.5'

COPY scripts/receptor /usr/bin/receptor
RUN mkdir -p /var/run/receptor
CMD git lfs install --system
CMD rm -rf /output

#Remediation steps below
RUN yum install xz-libs -y
RUN yum install subversion -y
RUN yum install subversion-libs -y
RUN yum install python3 -y
RUN yum install python3-libs -y
RUN yum install python-unversioned-command -y
RUN yum install libksba -y
RUN yum install git-core -y
RUN yum install vim-minimal -y
#Remediation steps complete

USER 1000
CMD chmod a+x /opt/builder/bin/entrypoint
ENTRYPOINT ["/opt/builder/bin/entrypoint","dumb-init"]
CMD ["bash"]
