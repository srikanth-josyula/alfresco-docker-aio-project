ARG SHARE_TAG
FROM docker.io/alfresco/alfresco-share:${SHARE_TAG}

ARG TOMCAT_DIR=/usr/local/tomcat

# default user is alfresco (added on the base image alfresco/alfresco-content-repository-community)
# change to root user to be able to install the addons and packages
USER root

# Install modules and addons
# RUN mkdir -p $TOMCAT_DIR/amps_share
ADD amps_share/*.amp $TOMCAT_DIR/amps_share
ADD jars/*.jar $TOMCAT_DIR/webapps/share/WEB-INF/lib

RUN java -jar $TOMCAT_DIR/alfresco-mmt/alfresco-mmt*.jar install $TOMCAT_DIR/amps_share $TOMCAT_DIR/webapps/share -directory -nobackup -verbose -force

# give full permissions for now
RUN chmod -R 777 ${TOMCAT_DIR}/webapps && \
    chmod -R 777 ${TOMCAT_DIR}/shared