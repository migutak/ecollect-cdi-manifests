FROM tomcat:9.0

RUN apt-get update && apt-get install wget unzip zip -y

# To fix 404 on tomcat image
RUN mv webapps webapps2 && mv webapps.dist/ webapps

COPY birt_live /usr/local/tomcat/webapps/birt/

#Add JDBC
COPY ojdbc8.jar /usr/local/tomcat/webapps/birt/WEB-INF/lib

#Add custom configs
COPY server-uat.xml /usr/local/tomcat/conf/server.xml
COPY tomcat-users.xml /usr/local/tomcat/conf/tomcat-users.xml
COPY context.xml /usr/local/tomcat/conf/context.xml

# Map Reports folder
VOLUME /usr/local/tomcat/webapps/birt/reports
VOLUME /usr/local/tomcat/webapps/birt

#Start
CMD ["catalina.sh", "run"]

#Port
EXPOSE 8080

# docker build -t migutak/birt-uat:1.1 .