Example maven project for deploying jsgilmore/gostorm based bolts to a Storm cluster.

## Building

The Golang example code for this bolt is in [src/go/splitsentence.go](src/go/splitsentence.go)

Maven is used to create a jar file:

```bash
mvn package
```

This will call the go build process inside the `pom.xml` and will result in a Topology JAR file `target/gostorm-runner-X.jar`.


## Running Locally

```bash
storm jar target/gostorm-runner-1.1.1.jar com.sixgill.gostorm.Topology
```

## Running Locally using Docker

```bash
docker run -it -v $(pwd)/target/gostorm-runner-1.1.1.jar:/topology.jar storm storm jar /topology.jar com.sixgill.gostorm.Topology
```

## Submitting to a Storm cluster

Make sure nimbus is configured in `~/.storm/storm.yaml`, e.g:

```yaml
nimbus.seeds: ["127.0.0.1"]
```

Then deploy the topology with the following command:

```bash
storm jar target/gostorm-runner-1.1.1.jar com.sixgill.gostorm.Topology my-topology-name remote
```

## Customization

 1. Fork this repo
 2. Change the go package main to build in pom.xml
 3. Modify Topology.java.
