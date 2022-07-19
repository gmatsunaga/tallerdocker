FROM amazoncorretto:8

RUN yum install -y shadow-utils && useradd balanz

COPY passwordapi.jar /tmp/passwordapi.jar

RUN chown balanz:balanz /tmp/passwordapi.jar

CMD ["java","-jar","/tmp/passwordapi.jar"]

EXPOSE 8080

USER balanz