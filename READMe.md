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