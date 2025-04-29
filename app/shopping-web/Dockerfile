# 빌드 단계
FROM maven:3.8.6-openjdk-11-slim AS build

# 작업 디렉토리 설정
WORKDIR /workspace/source/app/shopping-web  # Tekton의 작업공간에 맞게 수정

# 소스 파일 복사
COPY . /workspace/source/app/shopping-web  # Tekton의 작업공간에 맞게 수정

# Maven을 사용하여 애플리케이션 빌드 (패키징)
RUN mvn clean package -DskipTests

# 실행 단계
FROM openjdk:11-jre-slim

# 빌드된 JAR 파일을 복사
COPY --from=build /workspace/source/app/shopping-web/target/shopping-web-*.jar /shopping-web.jar  # Tekton의 작업공간에 맞게 수정

# 애플리케이션 실행
ENTRYPOINT ["java", "-jar", "/shopping-web.jar"]

# 외부에서 접근할 포트
EXPOSE 8090
