#Maven Helpers
Several helper POM files.

##Dependency Executor
Maven will execute a main class with optional arguments from a dependency. The dependency group, artifact, version, main class and arguments may be configured via command line or by editing the properties in the POM.

###Example
The POM file includes as example:
* Dependency: [Apache Any23](https://any23.apache.org/)
* Main class: org.apache.any23.cli.ToolRunner
* Arguments: "rover http://www.lassila.org/ora.rdf#me -f turtle"

Execute the dependency and main class with the same arguments included in the POM file:
```bash
mvn clean test
```

Execute the same dependency and main class with the same arguments via command line:
```bash
mvn clean test -Dgroup=org.apache.any23 -Dartifact=apache-any23-core -Dversion=0.9.0 -Dmain=org.apache.any23.cli.ToolRunner -Dexec.args="rover http://www.lassila.org/ora.rdf#me -f turtle"
```

##Dependency Wrapper
Maven will package an executable JAR file including all dependencies. The dependency group, artifact, version and main class may be configured via command line or by editing the properties in the POM.

###Example
The POM file includes as example:
* Dependency: [Jersey](https://jersey.java.net/) hello world example
* Main class: org.glassfish.jersey.examples.helloworld.App

Package the dependency and main class included in the POM file:
```bash
mvn clean package
```

Package the same dependency and main class via command line:
```bash
mvn clean package -Dgroup=org.glassfish.jersey.examples -Dartifact=helloworld -Dversion=2.5.1 -Dmain=org.glassfish.jersey.examples.helloworld.App
```

Execute the main class included in the JAR file:
```bash
java -jar target/dependency-wrapper-0.0.2-shaded.jar
```