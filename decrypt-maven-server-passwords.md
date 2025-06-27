Add the following build extension to any pom file 
```xml
        <extensions>
            <extension>
                <groupId>com.github.shyiko.servers-maven-extension</groupId>
                <artifactId>servers-maven-extension</artifactId>
                <version>1.3.0</version>
            </extension>
        </extensions>
```
Then execute 
```bash
mvn properties:write-project-properties -P<profile> -Dproperties.outputFile=build.properties
```