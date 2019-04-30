# Quarkus demo: Infinispan Client

This example showcases how to use the Infinispan client with Quarkus. 

# Start the Infinispan server

You have two options:

**Option 1:** Running with Docker `docker run -it -p 11222:11222 jboss/infinispan-server:latest`

There is a known issue between Docker For Mac and Infinispan Client integration. Explanations can be found in
the following blog post [here](https://blog.infinispan.org/2018/03/accessing-infinispan-inside-docker-for.html)
You **won't need to do this in production**, but for Docker for Mac users we have:
- Created a file called `hotrod-client.properties` under `src/main/resources/META-INF/`
- Configured the following property: `infinispan.client.hotrod.client_intelligence=BASIC`

**Option 2:** Download the server (e.g. 9.4 or 10.0) from `http://www.infinispan.org/` and run `./bin/standalone.sh`

Infinispan Server listens in `localhost:8080` for REST endpoints.

To avoid conflicts, the quickstart configures another HTTP port in the [configuration file](/src/main/resources/application.properties) 
with the following property:

`
quarkus.http.port=8081
`

# Run the demo

- Run `mvn clean package` and then `java -jar ./target/quarkus-quickstart-runner.jar`
- In dev mode `mvn clean compile quarkus:dev`

Go to `http://localhost:8081/infinispan`, it should show you a message coming from the Infinispan server.