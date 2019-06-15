FROM centos:centos7.6.1810

#Variable for ops manager version
ENV opsmgsver=4.0.12.50517.20190605T1533Z-1

#for quicker development download file once locally then use with below line
#COPY mongodb-mms-4.0.12.50517.20190605T1533Z-1.x86_64.rpm ~/downloads/

#Install dependencies, wget for doing --no-check-certificate behind firewall if curl -kO does not work
RUN yum makecache fast \
    && yum install -y wget openssl net-tools \
    && yum clean all

#Get and install Ops Manager, remove rpm to make image smaller
RUN mkdir -p /downloads/ \
    && mkdir -p /opsuser/
WORKDIR /downloads/

RUN curl -O https://downloads.mongodb.com/on-prem-mms/rpm/mongodb-mms-${opsmgsver}.x86_64.rpm \
    && yum localinstall -y mongodb-mms-${opsmgsver}.x86_64.rpm \
    && yum clean all \
    && rm -f mongodb-mms-${opsmgsver}.x86_64.rpm 

#Expose Ports
EXPOSE 8080/tcp


COPY docker-entrypoint.sh /opsuser/docker-entrypoint.sh
WORKDIR /opsuser/
RUN chmod +x docker-entrypoint.sh

#Start ops manager
ENTRYPOINT [ "/opsuser/docker-entrypoint.sh" ]

CMD ["mongodb-mms"]