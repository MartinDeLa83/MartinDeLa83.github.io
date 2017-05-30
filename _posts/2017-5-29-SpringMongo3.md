---
layout: post
title: Spring Boot + Servicio REST (CRUD) + MongoDB (Windows 10) 3/3!
---

**Creando servicio REST con Spring DATA**

Vamos a a crear nuestro servicio REST sobre una colección sencilla (usuario) que contemplará las operaciones de:
INSERCCIÓN,CONSULTA,ACTUALIZACIÓN Y BORRADO (CRUD).

- Definimos la clase usuario que va a ser una entidad y que va a estar asociada con la colección de MongoDB usuario.
Los ids de cada documento en Mongo es un String que genera el propio motor de Mongo

~~~

A diferencia de bases de datos relacionales tenemos @Document en vez de @Entity

@Document(collection = "usuarios")
public class Usuario {
	
	@Id
	private String id;
	private String nombre;
	private String apellidos;
	private int edad;
	
	Se omiten getter y setters
	
~~~

- Definimos la interfaz UsuarioMongoRepository que va a heredar MongoRepository (y realizando esto ya no tenemos que definir los métodos tipicos de la interfaz, Spring Data los tiene implementados).

~~~

//Podemos definir querys a medida

public interface UsuarioMongoRepository extends MongoRepository<Usuario, Long> {
    Usuario findByNombre(String nombre);
    Usuario findById(String id);
}
~~~

- Para finalizar necesitamos nuestro rest controller donde se ejecutarán las peticiones http

~~~

@RestController
@RequestMapping(path="/usuario")
public class UsuarioRestController {
	
	//Es necesario instanciar este repositorio para poder realizar las operaciones hacia mongo
	@Autowired
	private UsuarioMongoRepository repositorio;
	   
	@RequestMapping(method = RequestMethod.POST)
	public ResponseEntity insertar (@RequestBody Usuario usuario){		
		repositorio.insert(usuario);		
		return new ResponseEntity(HttpStatus.CREATED);
	}
	
	@RequestMapping(method = RequestMethod.GET)
	public ResponseEntity<List<Usuario>> listar (){						
		return new ResponseEntity(repositorio.findAll(),HttpStatus.OK);
	}
	
	@RequestMapping(path="/{id}",method = RequestMethod.GET)
	public ResponseEntity<Usuario> getUsuarioPorId (@PathVariable String id){
		return new ResponseEntity<Usuario>(repositorio.findById(id),HttpStatus.OK);
	}
	
	@RequestMapping(path="/{id}",method = RequestMethod.DELETE)
	public ResponseEntity borrarPorId (@PathVariable String id){
		repositorio.delete(repositorio.findById(id));
		return new ResponseEntity(HttpStatus.OK);
	}
	
	@RequestMapping(method = RequestMethod.PUT)
	public ResponseEntity actualizar (@RequestBody Usuario usuario){
		repositorio.save(usuario);
		return new ResponseEntity(HttpStatus.OK);
	}
~~~

- El proyecto quedaría más o menos así:

![_config.yml]({{ site.baseurl }}/images/SpringMongoWindows/STS.PNG)

- Con todo esto ya podemos probar nuestro servicio REST, por ejemplo con POSTMAN. 
Para ejecutar elproyecto spring boot run as->Spring Boot App. Se ejecutará un jar que que lleva un tomcat embebido y el servidor junto con el proyecto quedarán arrancados.

- El proyecto se puede descargar en [Github](https://github.com/MartinDeLa83/SpringBootMongo). Además lleva incluído en el raíz Usuario.postman_collection.json para poder importarlo en postman.





