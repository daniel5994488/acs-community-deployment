FROM alfresco/alfresco-share:6.2.0

ARG TOMCAT_DIR=/usr/local/tomcat

# Logs always under $TOMCAT/logs folder
RUN echo "cd $TOMCAT_DIR/logs" > $TOMCAT_DIR/bin/setenv.sh \
    && chmod +x $TOMCAT_DIR/bin/setenv.sh

# Install modules and addons
RUN mkdir -p $TOMCAT_DIR/amps_share
COPY modules/amps_share $TOMCAT_DIR/amps_share
COPY modules/jars $TOMCAT_DIR/webapps/share/WEB-INF/lib

RUN sed -i 's/<show-authorization-status>true/<show-authorization-status>false/g' $TOMCAT_DIR/webapps/share/WEB-INF/classes/alfresco/share-config.xml

#RUN java -jar $TOMCAT_DIR/alfresco-mmt/alfresco-mmt*.jar install \
#    $TOMCAT_DIR/amps_share $TOMCAT_DIR/webapps/share -directory -nobackup -force
