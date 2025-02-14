# гайд

### необходим рабочий и поднятый jenkins

далее:
1. cоздать Item -> pipeline
2. в pipeline вставить то, что лежит в jenkinsfile с заменой некоторых значений

3. локально поднять sonarqube в докере:
```docker pull sonarqube```
```docker run --name sonarqube -p 9000:9000 sonarqube```

дефолтные креды: admin admin
оттуда необходимо взять projectkey при создании проекта + взять токен из профиля

4. manage jenkins -> tools -> добавить jdk, maven
5. manage jenkins -> plugins -> available plugins -> sonarqube scanner
6. manage jenkins -> system -> SonarQube servers(добавить токен, projectkey)