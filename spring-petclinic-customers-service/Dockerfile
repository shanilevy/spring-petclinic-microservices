#Download image from artifactory
ARG REGISTRY=docker.artifactory
#FROM openjdk:11-jdk
#FROM $REGISTRY/openjdk:8-jdk-alpine
FROM $REGISTRY/openjdk:11-jdk


WORKDIR /app

#Define ARG Again -ARG variables declared before the first FROM need to be declered again
ARG REGISTRY=http://artifactory-unified-ha.soleng-us.jfrog.team/artifactory
MAINTAINER Shani Levy

# Download artifacts from Artifactory
RUN curl $REGISTRY/customer_service-maven-staging-amsterdam/org/springframework/samples/petclinic/client/spring-petclinic-customers-service/2.3.1/spring-petclinic-customers-service-2.3.1.jar --output server1.jar


# Set JAVA OPTS + Static file location
ENV STATIC_FILE_LOCATION="/app/package/target/dist/"
ENV JAVA_OPTS=""

# Fire up our Spring Boot app
ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Dspring.profiles.active=remote -Djava.security.egd=file:/dev/./urandom -jar /app/server1.jar" ]



#FROM openjdk:8-jdk-alpine
#VOLUME /tmp
#ADD target/*.jar app.jar
#ENV JAVA_OPTS="
#ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /app.jar" ]
