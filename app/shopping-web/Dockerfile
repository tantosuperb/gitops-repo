# 빌드 단계 (Maven 이미지 사용)
FROM maven:3.8.6-openjdk-11-slim AS build

# 작업 디렉토리 설정 (컨테이너 내에서 작업할 디렉토리)
WORKDIR /workspace/source/app/shopping-web

# GitOps 레포지토리에서 소스 코드 복사
COPY ./src /workspace/source/app/shopping-web/src
COPY ./pom.xml /workspace/source/app/shopping-web/

# Maven을 사용하여 애플리케이션 빌드 (패키징)
RUN mvn clean package -DskipTests

# 실행 단계 (OpenJDK JRE 사용)
FROM openjdk:11-jre-slim

# 빌드된 JAR 파일을 컨테이너에 복사
COPY --from=build /workspace/source/app/shopping-web/target/shopping-web-*.jar /shopping-web.jar

# 애플리케이션 실행 명령 설정
ENTRYPOINT ["java", "-jar", "/shopping-web.jar"]

# 외부에서 접근할 포트 설정
EXPOSE 8080
