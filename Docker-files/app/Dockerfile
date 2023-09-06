FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/hotsauce1861devops/vpro2.git
RUN cd vpro2 && mvn install

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="Brenton"

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=BUILD_IMAGE vpro2/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
WORKDIR /usr/local/tomcat/
VOLUME /usr/local/tomcat/webapps