# spring-boot-with-jib

Minimal Spring Boot project that shows how to use [jib](https://github.com/GoogleContainerTools/jib/tree/master/jib-maven-plugin#container-object) to create an OCI-compatible (Docker) image with gradle.

Jib is [not intended for including RUN commands](https://github.com/GoogleContainerTools/jib/blob/master/docs/faq.md#i-need-to-run-commands-like-apt-get)  like Docker.  Therefore, if you have OS packages that need to be installed or run at build-time, then you need to package that as a base image, and jib will layer on top of that base image.


Full blog: 

## Project initially created using Spring Intializer

[Spring Initializer Web UI](https://start.spring.io/)

```
id=spring-boot-with-jib
artifact_id="${id//-}"
SpringAppClassName=SpringMain
version="0.0.2-SNAPSHOT"
groupId="org.fabianlee"

curl https://start.spring.io/starter.zip \
    -d type=gradle-project \
    -d dependencies=web,prometheus,devtools,actuator \
    -d javaVersion=11 \
    -d bootVersion=2.7.0 \
    -d groupId=$groupId \
    -d artifactId=$artifact_id \
    -d name=$SpringAppClassName \
    -d baseDir=$id \
    -d version=$version \
    -o $id.zip

unzip $id.zip
cd $id
chmod +x ./gradlew
```


