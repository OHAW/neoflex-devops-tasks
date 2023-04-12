#FROM maven:3.8.6 AS build_step
#COPY . /build
#WORKDIR /build
#RUN ./mvnw package

FROM openjdk:19-jdk-alpine
ARG USER_ID=1000
ARG GROUP_ID=1000
RUN addgroup -g ${GROUP_ID} app \
    && adduser -u ${USER_ID} -G app -s /bin/sh -D app
USER app
WORKDIR /app
#COPY --from=build_step /build /app
COPY . /app
ENV NAME=null
ENTRYPOINT ["java", "-Xms512m", "-Xmx1024m", "-jar", "/app/target/servingwebcontent-0.0.1-SNAPSHOT.jar"]
EXPOSE 8080