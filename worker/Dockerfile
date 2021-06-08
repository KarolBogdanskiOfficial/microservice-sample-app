FROM maven:latest AS build  
COPY src /usr/src/app/src  
COPY pom.xml /usr/src/app  

CMD mvn -f /usr/src/app/ -X clean package