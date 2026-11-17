# Distributed Cloud Storage

An early Java / Spring Boot project for exploring cloud storage and distributed systems.

## Current status

The repository currently contains an application starter, a health endpoint, and an application-context test. File storage, upload/download APIs, replication, and distributed coordination are not implemented yet.

## Stack

- Java 25, as configured in `pom.xml`
- Spring Boot `4.2.0-SNAPSHOT` with Spring Web MVC
- Maven Wrapper configured for Maven `3.9.16`
- JUnit / Spring Boot test support

## Run locally

Install JDK 25 and make sure `JAVA_HOME` points to it. The first run needs internet access to download Maven and dependencies, including Spring snapshot artifacts.

```sh
git clone https://github.com/krishpatel3313/Distributed-Cloud-Storage.git
cd Distributed-Cloud-Storage
./mvnw spring-boot:run
```

On Windows, use `mvnw.cmd spring-boot:run`.

With the default configuration, check the endpoint in another terminal:

```sh
curl http://localhost:8080/health
```

Expected response:

```json
{"status":"ok"}
```

## Tests

```sh
./mvnw test
```

The existing `contextLoads` test checks that the Spring application context starts. It does not test storage behavior or the HTTP endpoint.

These commands reflect the checked-in configuration; a clean build has not yet been verified. The project currently depends on a Spring Boot snapshot, so dependency availability may affect setup.

## Code map

| File | Purpose |
| --- | --- |
| `src/main/java/cloudstorage/CloudstorageApplication.java` | Application entry point |
| `src/main/java/cloudstorage/HealthController.java` | `GET /health` endpoint |
| `src/main/resources/application.properties` | Application name |
| `src/test/java/cloudstorage/CloudstorageApplicationTests.java` | Application-context test |

## Possible next steps

- Define file metadata and upload/download API contracts.
- Implement and test storage on a single node.
- Add replication and failure handling after the single-node flow works.

These are proposed directions, not existing features.
