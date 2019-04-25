# TODO - Replace with an openjdk/alpine base image if possible
FROM adoptopenjdk/openjdk11
VOLUME /tmp
ARG JAR_FILE
COPY ${JAR_FILE} app.jar
# Turns on JMX to expose metrics
# TODO - Need to automatically set java.rmi.server.hostname
ENTRYPOINT ["java",\
    "-Dserver.port=9090",\
    "-Dspring.profiles.active=int",\
    "-Djava.security.egd=file:/dev/./urandom",\
    "-Dcom.sun.management.jmxremote=true",\
    "-Dcom.sun.management.jmxremote.local.only=false",\
    "-Dcom.sun.management.jmxremote.authenticate=false",\
    "-Dcom.sun.management.jmxremote.ssl=false",\
    "-Djava.rmi.server.hostname=transform-api",\
    "-Dcom.sun.management.jmxremote.port=9999",\
    "-Dcom.sun.management.jmxremote.rmi.port=9998",\
    "-jar",\
    "/app.jar"]
EXPOSE 9090 9998 9999