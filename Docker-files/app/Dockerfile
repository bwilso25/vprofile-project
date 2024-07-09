#running apt update and installing maven (maven eventually creates the artifact)

#clone the source code

#cd into that folder
#checkout the docker branch, switch to docker branch, run mvn install
#mvn install which will generate the artifact in the vprofile folder we cd'd into
#it will create a folder called target, which will house the artifact

#fetch the tomcat image
#remove the default artifact
#location is in tomcat docker documentation
#copy the artifact u made in the first command (BUILD_IMAGE) from vprofile target folder recently created to the webapps tomcat folder
#where the default artifact was deleted
#tomcat will run the process on port 8080 but u can still declare the port if u want

FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/hkhcoder/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="Bernard"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]