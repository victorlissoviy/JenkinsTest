# Jenkins Test Application

This is a Spring Boot application configured to be deployed as a WAR file on a Tomcat server.

## Project Structure

```
JenkinsTest/
├── build.gradle.kts           # Gradle build configuration with Spring Boot and WAR support
├── src/
│   └── main/
│       ├── java/
│       │   └── org/
│       │       └── jenkins/
│       │           ├── Main.java                  # Spring Boot application entry point
│       │           └── controller/
│       │               └── HomeController.java    # REST controller with endpoints
│       └── resources/
│           └── application.properties             # Spring Boot configuration
└── DEPLOYMENT.md              # Instructions for deploying to Tomcat
```

## Changes Made

The following changes were made to convert this project to a Spring Boot application that can be deployed as a WAR file:

1. **Build Configuration**:
   - Added Spring Boot and Spring Dependency Management plugins
   - Added WAR plugin for WAR packaging
   - Added Spring Boot Web and Tomcat dependencies
   - Configured the WAR file name

2. **Application Structure**:
   - Updated Main.java to be a Spring Boot application
   - Extended SpringBootServletInitializer for WAR deployment
   - Created a REST controller with endpoints for testing
   - Added application.properties with Spring Boot configuration

3. **Deployment**:
   - Created DEPLOYMENT.md with instructions for deploying to Tomcat

## Building the Application

To build the application, run:

```bash
./gradlew bootWar
```

This will generate a WAR file at `build/libs/jenkins-test.war`.

## Running the Application

### Option 1: Run as a Spring Boot Application

For development, you can run the application directly:

```bash
./gradlew bootRun
```

### Option 2: Deploy to Tomcat

See [DEPLOYMENT.md](DEPLOYMENT.md) for detailed instructions on deploying to Tomcat.

## Endpoints

- `/jenkins-test/` - Returns a welcome message
- `/jenkins-test/health` - Returns application health status

## Requirements

- Java 21
- Gradle (wrapper included)
- Tomcat 9.0+ (for deployment)