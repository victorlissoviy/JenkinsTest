# Deployment Instructions

This document provides instructions for deploying the Jenkins Test application WAR file to a Tomcat server.

## Prerequisites

- Apache Tomcat 9.0 or later installed
- Java 21 or compatible version installed (as specified in the project)

## Deployment Steps

### 1. Build the WAR file

If you haven't already built the WAR file, run the following command from the project root:

```bash
./gradlew bootWar
```

This will generate the WAR file at `build/libs/jenkins-test.war`.

### 2. Deploy to Tomcat

#### Option 1: Manual Deployment

1. Copy the WAR file to Tomcat's webapps directory:
   ```bash
   cp build/libs/jenkins-test.war /path/to/tomcat/webapps/
   ```

2. Start Tomcat if it's not already running:
   ```bash
   /path/to/tomcat/bin/startup.sh
   ```

3. Tomcat will automatically deploy the application.

#### Option 2: Using Tomcat Manager

1. Access the Tomcat Manager web interface (typically at http://localhost:8080/manager/html)
2. Log in with your Tomcat manager credentials
3. In the "WAR file to deploy" section, browse to the WAR file and click "Deploy"

### 3. Verify Deployment

1. Access the application at: http://localhost:8080/jenkins-test/
2. You should see a JSON response with a welcome message
3. Check the health endpoint at: http://localhost:8080/jenkins-test/health

## Configuration

The application is configured with the following settings:

- Context path: `/jenkins-test`
- Port: 8080 (default Tomcat port)

You can modify these settings in the `application.properties` file before building the WAR.

## Troubleshooting

- Check Tomcat logs at `/path/to/tomcat/logs/catalina.out` for any errors
- Ensure Tomcat is running with Java 21 or a compatible version
- Verify that the WAR file was successfully deployed by checking the Tomcat manager or the webapps directory

## Additional Information

- The application uses Spring Boot 3.2.3
- The application requires Java 21
- The WAR file includes all necessary dependencies except for the Tomcat server itself