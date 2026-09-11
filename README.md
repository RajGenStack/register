# Register App: Maven Multi-Module WAR with Jenkins CI

A Java web application with a user registration page, built as a Maven multi-module project, packaged and tested by a Jenkins pipeline, and runnable on Apache Tomcat in Docker.

![Java](https://img.shields.io/badge/Java_17-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=flat-square&logo=apachemaven&logoColor=white)
![Tomcat](https://img.shields.io/badge/Tomcat-F8DC75?style=flat-square&logo=apachetomcat&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white)

## Modules

| Module | Contents |
|---|---|
| `server` | A `Greeter` class with a JUnit test |
| `webapp` | The registration page (`index.jsp`), packaged as `webapp.war` |

## Jenkins pipeline

```mermaid
flowchart LR
    A["Clean workspace"] --> B["Checkout from GitHub"]
    B --> C["mvn clean package"]
    C --> D["mvn test"]
```

The pipeline runs on an agent labelled `Jenkins-Agent`, uses tools named `java17` and `Maven3`, and checks out with the `github` credentials.

## Build and run

```bash
mvn clean package
docker build -t register-app .
docker run -p 8080:8080 register-app
```

Open http://localhost:8080/webapp/.

The Dockerfile starts from `tomcat:latest`, restores Tomcat's default web apps and copies in `webapp/target/*.war`.

## Credits

The registration page comes from the Virtual TechBox DevOps course, as credited on the page itself.

---

<div align="center">
  <sub>Maintained by <a href="https://github.com/RajGenStack">Rajan Kumar</a> · <a href="https://www.linkedin.com/in/rajan-kumar42">LinkedIn</a></sub>
</div>
