# OpenTelemetry Java Instrumentation Reproducer

## Build the project

```bash
mvn clean package
```

## Reproduce behavior change

### Run the application without the agent

```bash
java -jar target/spring-boot-sample-actuator-2.1.8.jar
```

Call the endpoint:

```bash
curl http://localhost:8080/report/6523 -I
```

Notice the HTTP Response code is 403.

### Run the application with the agent

```bash
java -javaagent:/path/to/opentelemetry-javaagent-all.jar -jar target/spring-boot-sample-actuator-2.1.8.jar
```

Call the endpoint:

```bash
curl http://localhost:8080/report/6523 -I
```

Notice the HTTP Response code is 406.
