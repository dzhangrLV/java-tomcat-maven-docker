# java-tomcat-maven-docker
Build and deploy a Tomcat-War Web App on Docker \
(c) Leonid Gorshkov 2019

Создается два образа:
1. Основа на debian: latest: \
устанавливаются пакеты git, maven, opendjk \
клонируется репозиторий boxfuse, после maven собирает war-пакет 
2. Рабочий образ с tomcat: \
собирается web-сервер apache tomcat, из первого образа копируется файл .war в папку webapp \
и запускается. \

Результат вывода docker images \
REPOSITORY          TAG                 IMAGE ID            CREATED              SIZE \
hello               latest              aca39ffb0de1        About a minute ago   106MB \
none                none                3ff78ebd3ee0        2 minutes ago        698MB \
openjdk             8-jre-alpine        ce8477c7d086        2 weeks ago          84.9MB \
debian              latest              2d337f242f07        4 weeks ago          101MB \

Контейнер запускается командой: \
docker run -d -p 8080:8080 aca39ffb0de1

В браузере результат доступ по адресу: http://ip-адрес_сервера:8080/hello-1.0/