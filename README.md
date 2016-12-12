# Maven Assembly Example

This project is an example of how to use the
[Maven Assembly Plugin](https://maven.apache.org/plugins/maven-assembly-plugin/index.html)
to create a zip file containing both your built Java archive and a Cloud Foundry
manifest yaml file.

# How to build

```
git clone https://github.com/ECSTeam/assemblyexample.git
mvn install
```

# How to use in your project

Adapted from instructions
[here](https://maven.apache.org/plugins/maven-assembly-plugin/examples/sharing-descriptors.html).

Add the following lines to your `pom.xml`:

```xml
...
<build>
    ...
    <plugins>
        ...
        <plugin>
            <artifactId>maven-assembly-plugin</artifactId>
            <version>3.0.0</version>
            <dependencies>
                <dependency>
                    <groupId>com.ecsteam</groupId>
                    <artifactId>assembly-example</artifactId>
                    <version>1.0-SNAPSHOT</version>
                </dependency>
            </dependencies>
            <executions>
                <execution>
                <id>make-assembly</id>
                <phase>package</phase>
                <goals>
                    <goal>single</goal>
                </goals>
                <configuration>
                    <!-- This is where we use our shared assembly descriptor -->
                    <descriptorRefs>
                        <descriptorRef>application-with-manifest</descriptorRef>
                    </descriptorRefs>
                </configuration>
                </execution>
            </executions>
        </plugin>
        ...
    </plugins>
    ...
</build>
...
```
