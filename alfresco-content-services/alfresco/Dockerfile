ARG ALFRESCO_TAG
FROM docker.io/alfresco/alfresco-content-repository-community:${ALFRESCO_TAG}

ARG TOMCAT_DIR=/usr/local/tomcat

# default user is alfresco (added on the base image alfresco/alfresco-content-repository-community)
# change to root user to be able to install the addons and packages
USER root

# Install modules and addons
# RUN mkdir -p $TOMCAT_DIR/amps
ADD amps/*.amp $TOMCAT_DIR/amps
ADD jars/*.jar $TOMCAT_DIR/webapps/alfresco/WEB-INF/lib

RUN java -jar $TOMCAT_DIR/alfresco-mmt/alfresco-mmt*.jar install $TOMCAT_DIR/amps $TOMCAT_DIR/webapps/alfresco -directory -nobackup -verbose -force

# give full permissions for now
RUN chmod -R 777 ${TOMCAT_DIR}/webapps && \
    chmod -R 777 ${TOMCAT_DIR}/shared
