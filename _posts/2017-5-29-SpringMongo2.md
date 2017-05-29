---
layout: post
title: Spring Boot + Servicio REST (CRUD) + MongoDB (Windows 10) 2/3!
---

**2 Creando un Proyecto Spring Boot...**

Asumimos que tenemos ya instalado **spring tool suite**

- Creamos un nuevo proyecto: **new -> Spring Starter Project** 

![_config.yml]({{ site.baseurl }}/images/SpringMongoWindows/Captura1.PNG)

- Agregamos los starter **web y mongodb**

~~~

En el pom.xml...

<dependencies>
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-data-mongodb</artifactId>
	</dependency>
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-web</artifactId>
	</dependency>
</dependencies>
	
~~~

- Podemos ver que se nos ha generado una clase:  
**SpringBootMongoApplication** que es el **lanzador del proyecto spring boot**

- En src/main/resources encontramos un fichero application.properties que es en donde se agregan las configuraciones asociadas al proyecto spring boot.
En nuestro caso tendremos que editarlo para integrar la configuración de MongoDB:

~~~
#Como vamos a llamar a la bbdd
spring.data.mongodb.database=springbootMongo
#Dirección del servidor mongodb
spring.data.mongodb.host=localhost
#Puerto
spring.data.mongodb.port=27017
~~~



