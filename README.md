# Tahopen-Charbeans

#### Pre-requisites for building the project:
* Maven, version 3+
* Java JDK 11

#### Building it

__Build for nightly/release__

All required profiles are activated by the presence of a property named "release".

```
$ mvn clean install -Drelease
```

This will build, unit test, and package the whole project (all of the sub-modules). The artifact will be generated in: ```target```

__Build for CI/dev__

The `release` builds will compile the source for production (meaning potential obfuscation and/or uglification). To build without that happening, just eliminate the `release` property.

```
$ mvn clean install
```

#### Running the tests

__Unit tests__

This will run all unit tests in the project (and sub-modules).
```
$ mvn test
```

If you want to remote debug a single java unit test (default port is 5005):
```
$ cd core
$ mvn test -Dtest=<<YourTest>> -Dmaven.surefire.debug
```

__Integration tests__
In addition to the unit tests, there are integration tests in the core project.
```
$ mvn verify -DrunITs
```

To run a single integration test:
```
$ mvn verify -DrunITs -Dit.test=<<YourIT>>
```

To run a single integration test in debug mode (for remote debugging in an IDE) on the default port of 5005:
```
$ mvn verify -DrunITs -Dit.test=<<YourIT>> -Dmaven.failsafe.debug
```

__IntelliJ__

* Don't use IntelliJ's built-in maven. Make it use the same one you use from the commandline.
  * Project Preferences -> Build, Execution, Deployment -> Build Tools -> Maven ==> Maven home directory
