# гайд

### необходим рабочий и поднятый jenkins

далее:
1. cоздать Item -> pipeline
2. чекбокс на Github project, указать url
3. в pipeline вставить то, что лежит в jenkinsfile

4. локально поднять sonarqube в докере:
```docker pull sonarqube```
```docker run --name sonarqube -p 9000:9000 sonarqube```

дефолтные креды: admin admin

оттуда необходимо взять projectkey при создании проекта + взять токен из профиля

5. manage jenkins -> tools -> добавить jdk, maven