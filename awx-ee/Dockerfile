FROM quay.io/ansible/awx-ee
RUN pip install msal==1.24.1
USER root
RUN curl https://dl.rockylinux.org/pub/rocky/9/BaseOS/x86_64/os/Packages/x/xz-libs-5.2.5-8.el9_0.x86_64.rpm --output xz-libs-5.2.5-8.el9_0.x86_64.rpm
RUN yum install xz-libs-5.2.5-8.el9_0.x86_64.rpm -y
RUN curl https://dl.rockylinux.org/pub/rocky/9/AppStream/x86_64/os/Packages/s/subversion-libs-1.14.1-5.el9_0.x86_64.rpm --output subversion-libs-1.14.1-5.el9_0.x86_64.rpm
RUN yum install subversion-libs-1.14.1-5.el9_0.x86_64.rpm -y --allowerasing
RUN curl https://dl.rockylinux.org/pub/rocky/9/AppStream/x86_64/os/Packages/s/subversion-1.14.1-5.el9_0.x86_64.rpm --output subversion-1.14.1-5.el9_0.x86_64.rpm
RUN yum install subversion-1.14.1-5.el9_0.x86_64.rpm -y
RUN curl https://repo.almalinux.org/almalinux/9/AppStream/x86_64/os/Packages/git-core-2.39.3-1.el9_2.x86_64.rpm --output git-core-2.39.3-1.el9_2.x86_64.rpm
RUN yum install git-core-2.39.3-1.el9_2.x86_64.rpm -y
RUN curl https://dl.rockylinux.org/pub/rocky/9/BaseOS/x86_64/os/Packages/l/libksba-1.5.1-6.el9_1.x86_64.rpm --output libksba-1.5.1-6.el9_1.x86_64.rpm
Run yum install libksba-1.5.1-6.el9_1.x86_64.rpm -y
