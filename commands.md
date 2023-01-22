### Install SonarQube on Docker
```sh
docker run -d --name sonarqube -e SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true -p 9000:9000 sonarqube:latest
```

- Now create a Project on SonarQube

- After everything is setup you need to use the sonar-scanner to analyze all project files on it

### Use sonar-scanner using Docker

- There's no need to install sonar-scanner on your machine, you can use it through Docker.

- On the project folder run this command:

```sh
docker run \                   
    --rm \
    -e SONAR_HOST_URL="http://host.docker.internal:9000" \
    -e SONAR_SCANNER_OPTS="-Dsonar.projectKey=$YOUR_PROJECT_NAME" \
    -e SONAR_LOGIN="$YOUR_PROJECT_KEY" \
    --mount type=bind,source=$(pwd),target=/usr/src \
    sonarsource/sonar-scanner-cli
```