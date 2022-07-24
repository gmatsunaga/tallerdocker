FROM amazoncorretto:8-alpine3.14-jre

RUN adduser -D balanz

COPY passwordapi.jar /deployments/passwordapi.jar

RUN chown balanz:balanz /deployments/passwordapi.jar

EXPOSE 8080

USER balanz

CMD ["java","-jar","/deployments/passwordapi.jar"]


