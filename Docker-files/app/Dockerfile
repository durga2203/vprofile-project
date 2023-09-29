FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/durga2203/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcate:9-jre11
LABEL"project"="Vprofile"
LABLE"Author"="durga"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war usr/local/tomcat/webapps/ROOT.war
 
EXPOSE 8080
(CMD ["catalina.sh", "run"]):