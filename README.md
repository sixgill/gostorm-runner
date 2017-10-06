Example maven project for deploying jsgilmore/gostorm based bolts to a Storm cluster.

## Usage

Build the sentencesplit example from gostorm and package it into the jar:

```
go get github.com/jsgilmore/gostorm
mvn package
```

Run it in a local docker storm:

```
docker run -it -v $(pwd)/target/gostorm-runner-1.1.1.jar:/topology.jar storm storm jar /topology.jar com.sixgill.gostorm.Topology
```

## Customization

 1. Fork this repo
 2. Change the go package main to build in pom.xml
 3. Modify Topology.java.
