Setup of basic gradle using cli:
```
gradle init --type java-application --dsl groovy
```
The above command will setup a basic gradle project

```
./gradlew tasks
```
The above command act as a helper
```
./gradlew build
```
The above command can build your project

To prepare a jar which is executable, you need to setup manifest property in build.gradle to identify what is the main class to execute:
```
vi build.gradle
i, 
jar {
manifest {
attributes (
'Main-Class': 'org.example.Main'
)
}
}
esc, :wq
```

```
./gradlew jar
```
The above command creates a new jar file in build/libs folder

```
java -jar build/libs/filename.jar
```
The above command will execute your code

As we have included okhttp dependency in our build.gradle to make http request
using our plain java code. The below command wont work to build jar.
```
./gradlew jar
```
we need to add this line in plugin of build.gradle and use the below command 
```
plugins {
    id 'java'
    // Add the below line for building fat jar
    id 'com.gradleup.shadow' version '9.3.0'
}
```
```
./gradlew shadowJar
```
Note : A fat JAR (also known as an Uber JAR) is a single, self-contained Java archive file 
that includes not only your application's compiled code 
but also all of its required third-party libraries and dependencies.