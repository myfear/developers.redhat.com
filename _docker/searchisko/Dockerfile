FROM developer.redhat.com/java

RUN yum -y install mysql && \
    yum clean all

# Install JBoss EAP
RUN curl http://yum.engineering.redhat.com/pub/yum/repo_files/rhel6-jboss-eap-6-from-rhn.repo > /etc/yum.repos.d/rhel6-jboss-eap-6-from-rhn.repo && \
    yum install jbossas-standalone -y

# Install Searchisko
RUN curl http://download.devel.redhat.com/brewroot/packages/org.searchisko-parent/1.1.1/1/noarch/searchisko-api-1.1.1-1.el6.noarch.rpm > /searchisko.rpm && \
    yum -y install /searchisko.rpm && \
    rm /searchisko.rpm

ADD ./overlay /
RUN unzip /searchisko.sql.zip

EXPOSE 8080 8080

COPY run.sh /run.sh
CMD ["/bin/bash", "/run.sh"]
