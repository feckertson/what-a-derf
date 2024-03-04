# Debugging a Java RCP application
In eclipse, create a **Debug** configuration of type "Remote Java Application". 
- The project doesn't really matter. Perhaps one with source code for a plugin being debugged. 
- Connection Type = Standard (Socket Attach)
- Host = localhost
- Port = 1044  (or other, but match the value below)

Add the following lines to the `-vmargs` of the ini file:
```
-Xdebug
-Xrunjdwp:transport=dt_socket,server=y,suspend=n,address=1044
```

First launch the application. Then launch the debug configuration. 
After that, eclipse will stop at breakpoints set in the source code.

The fun part is obtaining and specifiying source files, especially when you don't know what needs to be debugged. 
To that end obtain the source jars by running something like the following on the assembly pom.  
`mvn dependency:copy-dependencies -Dclassifier=sources -DincludeGroupIds=com.cerner.bedrock,com.cerner.discern [-DoutputDirectory=destination]`  
Filter in relevant stuff and filter out irrelevant stuff with comninations of  
`-DincludeGroupIds`, `-DincludeArtifactIds`, `-DexcludeGroupIds`, `-DexcludeArtifactIds`, etc.

Extract the source jars by running the following command in the directory containing them noting that 
the parent destination directory (sources in this case) must already exist.  
`find . -iname '*.jar' -printf "unzip -u -d ../../sources/%P %P\n" | sh`  
 

Then add the parent destination directory to the list of source code search locations 
for the debug configuration.
