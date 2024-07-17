FROM gradle:7 AS base

CMD ["bash"]

# test-and-build
FROM base AS test-and-build
COPY . /workspace
RUN chmod +x ./gradlew && ./gradlew build

# production
FROM openjdk:17 AS production
COPY --from=test-and-build /workspace/build/libs/api-0.0.1-SNAPSHOT.jar /app.jar
CMD ["java", "-jar", "/app.jar"]

