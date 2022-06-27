FROM openjdk:11
COPY ./passwordapi.jar /usr/app/
WORKDIR /usr/app
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "passwordapi.jar"]
