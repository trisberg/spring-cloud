Spring-cloud offers a simple way for JVM apps in cloud to access services and discover their own information during runtime with special support for Spring apps. It offers an extensibility mechanism to make it work on multiple clouds and a variety of cloud services. Through the abstraction of cloud connector, you can make it work with multiple clouds (we include two examples: Cloud Foundry and Heroku) without touching the spring-cloud project itself. Through the service connector abstraction, you can make it work with a variety of services (such as all the new ones on Cloud Foundry marketplace), again, without touching the spring-cloud project itself.

The core concepts used in this project are:

1. **Cloud Connector**: An interface that a cloud provider can implement to allow the rest of the library work with a Platform As a Service (PaaS) offering.
2. **Service Connector**: An object, such as `javax.sql.DataSource`, that represent a connection to a service.
3. **Service information**: Information about the underlying service such as host, port, and credentials.
4. **Application information**: Information about application and instance in which these libraries are embedded.

The project comprises of four subprojects:

1. **[core](spring-cloud-core)**: Core library that is cloud agnostic and Spring agnostic. Provides entry point for application developers that choose to programmatically access cloud services and application information. It also provides an extension mechanism to contribute cloud connectors and service connector creators.
2. **[spring-service-connector](spring-cloud-spring-service-connector)**: Library that provides service connectors creators for javax.sql.DataSource and various connection factories spring-data projects.
3. **[cloudfoundry-connector](spring-cloud-cloudfoundry-connector)**: Cloud connector for [Cloud Foundry](http://www.cloudfoundry.com).
4. **[heroku-connector](spring-cloud-heroku-connector)**: Cloud connector for [Heroku](http://www.heroku.com).

Getting Started
===============

The following assumes that you are using Maven.

Spring apps
-----------

Add the [`spring-service-connector`](spring-cloud-spring-service-connector) and one or more cloud connectors dependencies (it is okay to add more that one cloud connectors):

    <dependency>
    	<groupId>org.springframework.cloud</groupId>
    	<artifactId>spring-cloud-spring-service-connector</artifactId>
    	<version>1.0.0.RELEASE</version>
    </dependency>
    <!-- If you intend to deploy the app on Cloud Foundry, add the following -->
    <dependency>
    	<groupId>org.springframework.cloud</groupId>
    	<artifactId>spring-cloud-cloudfoundry-connector</artifactId>
    	<version>1.0.0.RELEASE</version>
    </dependency>
    <!-- If you intend to deploy the app on Heroku, add the following -->
    <dependency>
    	<groupId>org.springframework.cloud</groupId>
    	<artifactId>spring-cloud-heroku-connector</artifactId>
    	<version>1.0.0.RELEASE</version>
    </dependency>

Then follow instructions on [how you use the Java config and `<cloud>` namespace](spring-cloud-spring-service-connector). You can also follow the [instructions](spring-cloud-core) on using the core API directly.

Non-spring apps
---------------
Add the [`core`](core) and one or more cloud connectors dependencies (it is okay to add more that one cloud connectors):

    <dependency>
    	<groupId>org.springframework.cloud</groupId>
    	<artifactId>spring-cloud-core</artifactId>
    	<version>1.0.0.RELEASE</version>
    </dependency>
    <!-- If you intend to deploy the app on CloudFoundry, add the following -->
    <dependency>
    	<groupId>org.springframework.cloud</groupId>
    	<artifactId>spring-cloud-cloudfoundry-connector</artifactId>
    	<version>1.0.0.RELEASE</version>
    </dependency>
    <!-- If you intend to deploy the app on Heroku, add the following -->
    <dependency>
    	<groupId>org.springframework.cloud</groupId>
    	<artifactId>spring-cloud-heroku-connector</artifactId>
    	<version>1.0.0.RELEASE</version>
    </dependency>

Then follow the [instructions](spring-cloud-core) on using spring-cloud API.
