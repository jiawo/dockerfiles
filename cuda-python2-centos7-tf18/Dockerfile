from 736626079/inspur:base-cuda-python2-centos7

RUN pip uninstall -y tensorflow-gpu
RUN pip uninstall -y tensorboard
RUN pip install tensorflow-gpu==1.8.0

RUN pip install cython easydict pandas

RUN mv /etc/yum.repos.d/kolla-all.repo /etc/yum.repos.d/kolla-all.repo_bak && \
    wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo && \
    yum clean all && yum makecache

RUN yum install -y unzip make httpd
RUN yum install -y libSM-1.2.2-2.el7.x86_64 libXrender-0.9.10-1.el7.x86_64 libXext-1.3.3-3.el7.x86_64

RUN sed -i "s|\/var\/www\/html|\/opt\/autolabel|g" /etc/httpd/conf/httpd.conf && \
    rm -rf /etc/httpd/conf.d/welcome.conf

RUN rm -rf /etc/yum.repos.d/CentOS-Base.repo && \
    mv /etc/yum.repos.d/kolla-all.repo_bak /etc/yum.repos.d/kolla-all.repo