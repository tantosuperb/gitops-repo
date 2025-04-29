FROM eclipse-temurin:17-jre-alpine
WORKDIR /app
COPY build/libs/shopping-web-*.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]
