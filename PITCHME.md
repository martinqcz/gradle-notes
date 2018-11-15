
## Gradle Build Tool

*open-source build automation tool*

---
@title[Gradle build phases]
@snap[north]
Gradle build phases
@snapend

Gradle has three build phases
@ol[](true)
- initialization
- configuration
- execution
@olend

---
@title[GRADLE_USER_HOME]
@snap[north]
GRADLE_USER_HOME
@snapend

@ul
- wrapper distributions
- caches
- local properties
- local init scripts
@ulend

---
@title[Gradle wrapper]
@snap[north]
Gradle wrapper
@snapend

- distribution-type - all/bin
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
Documentation
https://docs.gradle.org/current/userguide/build_environment.html

@ul
- gradle.properties from project root directory
- gradle.properties from GRADLE_USER_HOME directory
- system properties (```-D<propertyName>=<value>```)
@ulend
@snapend


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
@[2-4](define repositories)
@[6-8](build script classpath)
@[12](apply build scan plugin)
@[14-17](configure plugin extension to aggree with publishing)

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
