---
name: Writing Java
description: Writing modern, maintainable Java code leveraging recent language features and the Spring ecosystem.
---

# Writing Java

## Workflows

### 1. Scaffold Spring Boot Project

Creates a Spring Boot project using Spring Initializr.

```bash
#!/bin/bash
# create-springboot-project.sh
# Usage: ./create-springboot-project.sh <artifact-id> <package-name>

ARTIFACT_ID=$1
PACKAGE_NAME=$2

if [ -z "$ARTIFACT_ID" ] || [ -z "$PACKAGE_NAME" ]; then
  echo "Usage: $0 <artifact-id> <package-name>"
  echo "Example: $0 my-service com.example.myservice"
  exit 1
fi

# Using Spring Initializr API
curl https://start.spring.io/starter.zip \
  -d dependencies=web,data-jpa,validation,actuator \
  -d type=maven-project \
  -d language=java \
  -d bootVersion=3.2.0 \
  -d baseDir="$ARTIFACT_ID" \
  -d groupId=com.example \
  -d artifactId="$ARTIFACT_ID" \
  -d name="$ARTIFACT_ID" \
  -d packageName="$PACKAGE_NAME" \
  -d javaVersion=17 \
  -o "$ARTIFACT_ID.zip"

unzip "$ARTIFACT_ID.zip"
rm "$ARTIFACT_ID.zip"

echo "Spring Boot project created: $ARTIFACT_ID"
```

### 2. Java Code Review

Review Java code for modern practices and Spring conventions.

1. **Version Check**: Is Java 17+ features (Records, Switch Expressions) used?
2. **Injection Check**: Is constructor injection used instead of field injection?
3. **Null Check**: Is `Optional` used correctly to avoid NPEs?
4. **Stream Check**: Are Streams used for collection processing where appropriate?
5. **Test Check**: Are tests written with JUnit 5 and Mockito?

## Feedback Loops

### 1. Unit Testing

* **Trigger**: Code change.
* **Action**: Run `mvn test` or `gradle test`.
* **Outcome**: Verify logic correctness and prevent regressions.

### 2. Static Analysis

* **Trigger**: CI Pipeline.
* **Action**: Run SonarQube or Checkstyle.
* **Outcome**: Maintain code quality and adherence to standards.
