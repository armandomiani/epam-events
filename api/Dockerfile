FROM marketplace.gcr.io/google/openjdk8

RUN apt update && apt -y install \
  curl \
  maven \
  vim

COPY src/ /app/src
COPY pom.xml /app
COPY mvnw /app/mvnw
COPY .mvn /app/.mvn

WORKDIR /app

RUN mvn clean \
    && ./mvnw -Dmaven.test.skip=true package \
    && mv target/*.jar target/app.jar

ENTRYPOINT ["java","-jar","/app/target/app.jar"]
