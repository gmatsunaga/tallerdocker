FROM amazoncorretto:8-alpine3.14-jre

RUN adduser -D balanz

COPY passwordapi.jar /tmp/passwordapi.jar

RUN chown balanz:balanz /tmp/passwordapi.jar

CMD ["java","-jar","/tmp/passwordapi.jar"]

EXPOSE 8080

USER balanz