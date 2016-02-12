---
layout: default
title: Project Maintenance
---

* Will be replaced with the ToC
{:toc}


## Maven

### Dependency Versions

Dagger depends on a variety of libraries which may require updating from
time to time.  Dagger defines these versions in maven properties within the
parent `pom.xml` like this:

```xml
<project>
  ...
  <properties>
    <guava.version>19.0</guava.version>
  </properties>
  ...
</project>
```

which are then used in maven property expressions that look like this:

```xml
...
      <groupId>com.google.guava</groupId>
      <artifactId>guava</artifactId>
      <version>${guava.version}</version>
...
```


A handy plugin is available that permits easy inspection of these versions,
including noting where more recent versions are available.

```shell
mvn -N versions:display-property-updates
```

Version properties will be evaluated and displayed like this:

```
...
[INFO] ------------------------------------------------------------------------
[INFO] Building Dagger (Parent) 2.1-SNAPSHOT
[INFO] ------------------------------------------------------------------------
[INFO]
[INFO] --- versions-maven-plugin:2.1:display-property-updates (default-cli) @ dagger-parent ---
[INFO]
[INFO] The following version properties are referencing the newest available version:
[INFO]   ${google.java.format.version} ............................. 0.1-alpha
[INFO]   ${auto.service.version} ..................................... 1.0-rc2
[INFO]   ${compile-testing.version} ...................................... 0.8
[INFO]   ${auto.common.version} .......................................... 0.5
[INFO]   ${javax.inject.version} ........................................... 1
[INFO]   ${guava.version} ...................................... 19.0-SNAPSHOT
[INFO] The following version property updates are available:
[INFO]   ${javax.annotation.version} .......................... 2.0.1 -> 3.0.1
[INFO]   ${auto.value.version} .................................... 1.0 -> 1.1
[INFO]   ${junit.version} ....................................... 4.11 -> 4.12
[INFO]   ${mockito.version} ............................. 1.9.5 -> 2.0.40-beta
[INFO]   ${truth.version} ....................................... 0.26 -> 0.28
[INFO]   ${javawriter.version} ................................ 2.5.0 -> 2.5.1
...
```

This can be used both to note `-SNAPSHOT` versions, and also to note where
it may be wise to increment versions.

