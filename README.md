# spring-boot-logging-demo

## Maven build

```
$ mvn clean package
```

## Docker build

```
$ docker build -t logging-demo .

$ docker images
REPOSITORY                                  TAG                 IMAGE ID            CREATED             SIZE
logging-demo                                latest              1444f50dcadc        9 seconds ago       117M
```

## Run demo application

Run application with docker image.

```
$ docker run logging-demo 8080:8080
```

#Connect to localhost:8080 via web browser.#

#You can see "Hello World!" messages.#

## Connect to application via ssh and confirm log file

```
$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
d3af0da0160a        logging-demo        "java -Djava.securit…"   4 minutes ago       Up 4 minutes        0.0.0.0:8080->8080/tcp   gifted_ride

$ docker exec -it d3af0da0160a sh
/ # tail -f logs/spring-boot-logging.log 
[d3af0da0160a] 2018-09-06 04:15:46.155  INFO 1 --- [main] o.a.coyote.http11.Http11NioProtocol      : Starting ProtocolHandler ["http-nio-8080"]
[d3af0da0160a] 2018-09-06 04:15:46.170  INFO 1 --- [main] o.a.tomcat.util.net.NioSelectorPool      : Using a shared selector for servlet write/read
[d3af0da0160a] 2018-09-06 04:15:46.193  INFO 1 --- [main] s.b.c.e.t.TomcatEmbeddedServletContainer : Tomcat started on port(s): 8080 (http)
[d3af0da0160a] 2018-09-06 04:15:46.200  INFO 1 --- [main] com.example.demo.DemoApplication         : Started DemoApplication in 3.456 seconds (JVM running for 4.116)
[d3af0da0160a] 2018-09-06 04:28:59.250  INFO 1 --- [http-nio-8080-exec-1] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring FrameworkServlet 'dispatcherServlet'
[d3af0da0160a] 2018-09-06 04:28:59.251  INFO 1 --- [http-nio-8080-exec-1] o.s.web.servlet.DispatcherServlet        : FrameworkServlet 'dispatcherServlet': initialization started
[d3af0da0160a] 2018-09-06 04:28:59.276  INFO 1 --- [http-nio-8080-exec-1] o.s.web.servlet.DispatcherServlet        : FrameworkServlet 'dispatcherServlet': initialization completed in 25 ms
[d3af0da0160a] 2018-09-06 04:28:59.315  INFO 1 --- [http-nio-8080-exec-1] com.example.demo.HomeRestController      : logback example - info level
[d3af0da0160a] 2018-09-06 04:28:59.316  WARN 1 --- [http-nio-8080-exec-1] com.example.demo.HomeRestController      : logback example - warn level
[d3af0da0160a] 2018-09-06 04:28:59.316 ERROR 1 --- [http-nio-8080-exec-1] com.example.demo.HomeRestController      : logback example - error level

```


