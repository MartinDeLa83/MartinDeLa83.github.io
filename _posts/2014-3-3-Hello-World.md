---
layout: post
title: Spring Boot + Servicio REST (CRUD) + MongoDB (Windows 10)!
---

1. **Instalando MongoDB...**

He seguido la documentación oficial: https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/
Pero los pasos serían:

- Descargar MSI https://www.mongodb.com/download-center#community (sólo aplica en arquitecturas de x64 bits)
- Instalar MSI con la configuración por defecto (C:\Program Files\MongoDB)
- Para almacenar las bases de datos es necesario crear las carpetas C:\data\db (está es la ubicación por defecto. Si queréis que esté en otra ruta investigad en la documentación oficial)
- Para levantar la BBDD es necesario ejecutar el exe: C:\Program Files\MongoDB\Server\3.4\bin\mongod.exe
- Para abrir la consola: C:\Program Files\MongoDB\Server\3.4\bin\mongo.exe
- En la consola podemos teclear>show databases...

2. **Creando un Proyecto Spring Boot...**
- Asumimos que tenemos ya instalado spring tool suite
- Cremos un nuevo proyecto: new -> Spring Starter Project 
- Agregamos las dependencias web y mongodb
- Podemos ver que se nos ha generado una clase:  
SpringBootMongoApplication que es lanzador del proyecto spring boot
- En src/main/resources encontramos un fichero application.properties que es en donde se agregan las configuraciones asociadas al proyecto spring boot
En nuestro caso tendremos que editarlo para integrar la configuración de MongoDB



