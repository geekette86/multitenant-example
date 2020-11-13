<<<<<<< HEAD
Thank you for https://github.com/elgris/microservice-app-example for the source code of a microserice application , i used it directly to create my helmcharts and prove the multi-tenancy architecture after. Thank you @elgris
 
# What is multi-tenant architecture ?
 
SAAS solution in most of case are implemented base on two types of architecture ( I don't know if i can say architecture or pattern) multi tenant or multi instance , today we will talk about MT
so MT means many clients use one application instance and it can be replicated.The advantages of this approach are:
1. Doesn't really cost so much since resources are shared between different clients
2. it is more simple ( kind of ) 
3. Update one for all

what we will do here is just to have an unique namespace for every tenant so just fire up

```
helm install --set name=test ./demo
```
The command will deploy all the services and also will take `--name` and fire it in namespace.yaml and this how we can duplicate the services for every tenant 

=======
>>>>>>> f2b51f4... init project
# Example microservice app

This is an example of web application comprising of several components communicating to each other. In other words, this is an example of microservice app. Why is it better than many other examples? Well, because these microservices are written in different languages. This approach gives you flexibility for running experiments in polyglot environment.

The app itself is a simple TODO app that additionally authenticates users. I planned to add some admin functionality, but decided to cut the scope and add it later if needed.

## Components

1. [Frontend](/frontend) part is a Javascript application, provides UI. Created with [VueJS](http://vuejs.org)
2. [Auth API](/authapi) is written in Go and provides authorization functionality. Generates JWT tokens to be used with other APIs.
3. [TODOs API](/todosapi) is written with NodeJS, provides CRUD functionality ove user's todo records. Also, it logs "create" and "delete" operations to Redis queue, so they can be later processed by [Log Message Processor](/logmessageprocessor).
4. [Users API](/usersapi) is a Spring Boot project written in Java. Provides user profiles. Does not provide full CRUD for simplicity, just getting a single user and all users.
5. [Log Message Processor](/logmessageprocessor) is a very short queue processor written in Python. It's sole purpose is to read messages from Redis queue and print them to stdout
6. [Zipkin](https://zipkin.io). Optional 3rd party system that aggregates traces produced by other components.

Take a look at the components diagram that describes them and their interactions.
![microservice-app-example](https://user-images.githubusercontent.com/1905821/34918427-a931d84e-f952-11e7-85a0-ace34a2e8edb.png)

## Use cases

- Evaluate various instruments (monitoring, tracing, you name it): how easy they integrate, do they have any bugs with different languages, etc.

## How to start

The easiest way is to use `docker-compose`:

```
docker-compose up --build
```

Then go to http://127.0.0.1:8080 for web UI. [Zipkin](https://zipkin.io) is available on http://127.0.0.1:9411 by default.

## Contribution

This is definitely a contrived project, so it can be extended in any way you want. If you have a crazy idea (like RESTful API in Haskell that counts kittens of particular user) - just submit a PR.

## License

MIT
