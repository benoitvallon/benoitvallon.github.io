---
layout:     post
title:      "Getting started with Spring Boot"
subtitle:   "Generate your first Spring project in 5 minutes"
date:       2016-04-30 23:56:40
author:     "Benoit VALLON"
header-img: "/img/2016-04-30-getting-started-with-spring-boot/post-getting-started-with-spring-boot.jpg"
comments:   true
categories: tips
tags:       [spring boot, spring, java]
---

# What is Spring Boot

Spring Boot is a tool provided by Spring to help you starting a project quickly and easily. This is indeed true, but not the first time.

If you are using Spring Boot for the first time it will take you some time to get all the pieces of the long documentation to really understand how to use it. Spring Boot is simple but I think the documentation doesn't really show it.

# Don't get confused...

If you want to work with Spring Boot you will inevitably go there [http://projects.spring.io/spring-boot](http://projects.spring.io/spring-boot). This page is very confusing because you will understand that Spring Boot is a CLI, but also an online tool, and finally the page will suggest you to download a snippet of `.xml`.

From here you should start be lost and ask yourself questions like, why do I need to download a snippet of code if there is a CLI? Is this Spring Boot thing a generator or not?

Then, to get more confused they add:

> The recommended way to get started using spring-boot in your project is with a dependency management system

Ok, now you are talking about a dependency management system although I just wanted to generate a boilerplate Spring project to start with. This is where you think that you will need to go to the heavy documentation to understand Spring Boot. The good news is that you don't need to.

# So, what is it really?

Spring Boot regroup 2 things.

Spring Boot will help you to:

- Generate a project
  - Using the online tool
  - Using the CLI
- Run/maintain your project by managing Spring dependencies for you.

# Generate a Spring project

## Using the online tool Spring Initializr

If you don't like the command line you can go online to [http://start.spring.io](http://start.spring.io) and generate your Spring project.

Be careful, by default the tool doesn't give you much choices, but on the bottom of the page you have a small link to access the full version of the tool.

The tool can take a lot of information as entries like the dependency management system that you want to use (Gradle or Maven), the Java version, or your Spring dependencies. After you have selected your desired options, the tool will send you a `.zip` file containing your Spring project and that's it, you are done.

## Using the CLI

The Spring Boot CLI provides a command which can generate a Spring project for you, like the Spring Initializr does. But if you prefer to use the CLI, you will have to install it first. It can be installed by several means but the easiest on Mac OS is surely Homebrew.

```shell
brew tap pivotal/tap
brew install springboot
```

Go [here](https://docs.spring.io/spring-boot/docs/current/reference/html/getting-started-installing-spring-boot.html) if you need instructions to install it on another system.

The command `spring init` will generate `.zip` file containing a very basic project structure but it is really helpful and powerful if you add some parameters to the command. Have a look at the documentation here  [https://docs.spring.io/spring-boot/docs/current/reference/html/cli-using-the-cli.html#cli-init](https://docs.spring.io/spring-boot/docs/current/reference/html/cli-using-the-cli.html#cli-init) to get an overview of the possibilities or type `spring init --list`. If you use all of them you can get something as complete as the online version of the Spring Initializr.

This is an example of the command that you could use:

```shell
spring init --build=maven --java-version=1.8 --dependencies=web --packaging=war sample-app.zip
```

# Run/manage your project with Spring Boot

The second use of Spring Boot is to run and maintain the dependencies of your project.

## Run your project

To run your project you would need to build it and then run it. But because Spring Boot sets up your project with a Maven plugin, it will do all of that for you.

So, in order to run your project with the help of Maven and Spring Boot, simply run:

```shell
mvn spring-boot:run
```

You should now be able to visit [http://localhost:8080](http://localhost:8080) and see the first page of your project.

Don't be surprised to read the message "Whitelabel Error Page" on the page. It doesn't mean that your project is not working but instead that your project doesn't have a page mapped to the url "/". So all what you need to do here is to create your first controller and start building your web app.

## Manage your Spring dependencies

Spring Boot is also very helpful to manage Spring dependencies in a project. Remember that when you generated your project you mentioned Spring dependencies. Those dependencies are indeed `spring-boot` dependencies which means that Spring Boot will manage them for you.

It will manage for example the versions to be sure that they are compatible but where it shines really is with configuration.

Spring Boot dependencies will allow your Spring project to be automatically configured whenever possible which is quite often actually. That means that your project almost doesn't require that you manage its configuration yourself. This is a big advantage.

Finally, Spring Boot Actuator aimed at helping you to monitor and manage your application with a set of metrics gathered automatically for you. It adds several endpoints to your application each of them relative to different metrics. Learn more [here](http://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#production-ready).

### Add other Spring dependencies

You are still able to add Spring dependencies after you generated your project. Go to your software management file and add the `sping-boot` dependencies that you want. This is an example with Maven.

```xml
...
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-tomcat</artifactId>
  <scope>provided</scope>
</dependency>
...
```

## A word on Gradle and Maven

Although the Maven plugin allows you to build and run your project as a single step, you can still of course use Gradle or Maven to only build your project in order to deploy it.

If you want to use those tool, here is a reminder of how to.

Install Maven:

```shell
brew install maven
```

Build your project with Maven:

```shell
mvn clean install
```

Once you have built your project you should get either a `.jar` or `.war` depending of what you chose when you generated your project. Then, you can run your project with:

```shell
java -jar target/sample-app-0.0.1-SNAPSHOT.jar
```

or (for a `.war`):

```shell
java -jar target/sample-app-0.0.1-SNAPSHOT.war
```

Finally, if you need to, you can also deploy your resulting `.war` file to a Tomcat server.
