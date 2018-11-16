
## Gradle Build Tool

*open-source build automation tool*

---
@title[Gradle build phases]
@snap[north]
Gradle build phases
@snapend

Gradle has three build phases
@ol[](true)
- Initialization
- Configuration
- Execution
@olend

---
@title[Initialization phase]
@snap[north]
Initialization phase
@spanend

---
@title[Configuration phase]
@snap[north]
Configuration phase
@spanend

---
@title[Execution phase]
@snap[north]
Execution phase
@spanend

---
@title[Gradle user home]
@snap[north]
Gradle user home directory
@snapend
- Defaults to $HOME/.gradle
- Could be configured by GRADLE_USER_HOME env
- Contains
	@ul
	- caches
		- artifact/module cache
		- script cache
		- build cache
	- wrapper distributions
	- daemon logs
	- local properties
	- local init scripts
	@ulend

---
@title[Gradle wrapper]
@snap[north]
Gradle wrapper
@snapend
Used to make sure that all are using the same Gradle version
Two types of distribution
- binary - just compiled classes
- all - contains sources and documentation
	- useful in IDE to have content assist
- example
```bash
$ gradle init --type java-library --dsl kotlin
```
---
@title[Properties lookup]
@snap[north]
Properties lookup
@snapend

@snap[west fragment]
During initialization Gradle reads properties.
Later values wins

Documentation
https://docs.gradle.org/current/userguide/build_environment.html

@ul
- gradle.properties from project root directory
- gradle.properties from GRADLE_USER_HOME directory
- system properties (```-D<propertyName>=<value>```)
@ulend
@snapend


---
@title[Gradle daemon]
@snap[north]
Gradle daemon
@snapend
- speeds up configuration phase by reusing result from previous run
- Daemons need to be compatible
	- java version
	- jvm properties
---
@title[Gradle daemon]
@snap[north]
Gradle daemon
@snapend
- prevent multiple incompatible daemons by setting *org.gradle.jvmargs* property in GRADLE_USER_HOME/gradle.properties
- idle timeout defaults to 3 hours
	- set custom timeout by setting *org.gradle.daemon.idletimeout* in GRADLE_USER_HOME/gradle.properties

---
@title[Init script]
@snap[north]
Init script
@snapend
- Init scripts are executed with every build
- Good place for local defaults
	- build scan
	- repositories
- location
	- $GRADLE_USER_HOME/init.d/\*.gradle
	- $GRADLE_USER_HOME/init.gradle

---
@title[build-scan.gradle]
@snap[north span-100]
build-scan.gradle
@snapend

```groovy
initscript {
    repositories {
        gradlePluginPortal()
    }

    dependencies {
        classpath 'com.gradle:build-scan-plugin:1.16'
    }
}

rootProject {
    apply plugin: com.gradle.scan.plugin.BuildScanPlugin

    buildScan {
        termsOfServiceUrl = 'https://gradle.com/terms-of-service'
        termsOfServiceAgree = 'yes'
    }
}
```
@[2-4](Define repositories with plugin dependencies)
@[6-8](Build script classpath)
@[12](Apply build scan plugin)
@[14-17](Configure plugin extension to aggree with publishing)

---
@title[Basic script objects]
@snap[north]
Basic script objects
@snapend
- configurations
- dependencies
- tasks
- plugins

---
@title[Build types]
@snap[north]
Build types
@snapend
- Single project build
- Multiproject build
- Composite build

---
@title[Single project build]
@snap[north]
Single project build
@snapend
- Just one project that only external dependencies

---
@title[Multiproject build]
@snap[north]
Multiproject build
@snapend
- more projects/libraries that are compiled together
- Gradle solves task execution order
- compilation results may be used immediatelly by another projects in the build

---
@title[Composite build]
@snap[north]
Composite build
@snapend
- When you need to modify code of the library together with code that uses that library
- No need to release and deploy to artifactory
- External dependencies that are produced by included builds are replaced as project dependencies

---
@title[Slide title]
@snap[north]
slide title
@snapend

```javascript
// Include http module.
var http = require("http");

// Create the server. Function passed as parameter
// is called on every request made.
http.createServer(function (request, response) {
  // Attach listener on end event.  This event is
  // called when client sent, awaiting response.
  request.on("end", function () {
    // Write headers to the response.
    // HTTP 200 status, Content-Type text/plain.
    response.writeHead(200, {
      'Content-Type': 'text/plain'
    });
    // Send data and end response.
    response.end('Hello HTTP!');
  });

// Listen on the 8080 port.
}).listen(8080);
```

@snap[south span-100]
@[1-3](Hello this is nice example)
@[1,2](You can present code inlined within your slide markdown too.)
@[9-17](Displayed using code-syntax highlighting just like your IDE.)
@[19-20](Again, all of this without ever leaving your slideshow.)
@snapend

---?gist=onetapbeyond/494e0fecaf0d6a2aa2acadfb8eb9d6e8&lang=Scala&title=GIST: Scala Snippet

---
first title
aaa
- xyz
- abc
- qwerty
	- abc
	- xyz
* alfa
** beta
** gama
* delta

---
@title[Last slide]

@snap[north]
settings.gradle
@snapend

```groovy
// my comment
pluginManagement {
	repositories {
		mavenLocal()
	}
}
```
