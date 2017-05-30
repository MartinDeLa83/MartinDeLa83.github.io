---
layout: post
title: Spring Boot + Servicio REST (CRUD) + MongoDB (Windows 10) 1/3!
---

**1 Instalando MongoDB...**

He seguido la documentación oficial: [MongoDB para Windows DOC](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/)
Pero los pasos serían:

- Descargar MSI [MongoDB para Windows instalador](https://www.mongodb.com/download-center#community) (sólo aplica en arquitecturas de x64 bits)

- Instalar MSI con la configuración por defecto (*C:\Program Files\MongoDB*)

- Para almacenar las bases de datos es necesario crear las carpetas C:\data\db (está es la ubicación por defecto. Si queréis que esté en otra ruta investigad en la documentación oficial)

- Para levantar la BBDD es necesario ejecutar el exe: **C:\Program Files\MongoDB\Server\3.4\bin\mongod.exe**

- Para abrir la consola: **C:\Program Files\MongoDB\Server\3.4\bin\mongo.exe**

- En la consola podemos teclear>show databases...

![_config.yml]({{ site.baseurl }}/images/SpringMongoWindows/mongodb.PNG)

En mongoDB podemos hacer la siguiente relación: una colección es una tabla y un documento una fila.


~~~
Ejemplo: En la colección users existen 2 documentos
 db.users.find()
{ "_id" : ObjectId("592300c295fa5900ffc27363"), "name" : "Martin", "age" : 34 }
{ "_id" : ObjectId("592300f795fa5900ffc27364"), "name" : "Juan", "age" : 45 }
~~~