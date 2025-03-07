# Crear un sistema CRUD para gestionar propiedades 💻

El propósito de este proyecto es desarrollar un sistema CRUD (Crear, Leer, Actualizar, Eliminar) para la gestión de propiedades inmobiliarias. La aplicación web permitirá a los usuarios administrar anuncios de propiedades de manera eficiente a través de una interfaz intuitiva y un backend robusto.

Los usuarios podrán:
✅ Crear nuevas propiedades agregando información detallada.
✅ Visualizar una lista de propiedades disponibles y acceder a los detalles de cada una.
✅ Actualizar los datos de una propiedad existente en caso de modificaciones.
✅ Eliminar propiedades que ya no estén disponibles.

Para lograr esto, la aplicación se desarrollará con Spring Boot para el backend, MySQL como base de datos, y un frontend en HTML, JavaScript y AJAX (o Fetch API) para una experiencia de usuario fluida. Además, se desplegará en AWS, asegurando escalabilidad y disponibilidad.

## Componentes del Proyecto.

1- Backend (Spring Boot)

Controladores: Manejan las solicitudes HTTP y definen los endpoints de la API.
Entidades: Representan las tablas de la base de datos.
Repositorios: Proveen métodos para realizar operaciones CRUD en la base de datos.

2- Frontend (HTML, CSS, JavaScript)

HTML: Define la estructura de la página web.
CSS: Aplica estilos a la página web.
JavaScript: Maneja la lógica del frontend, incluyendo la interacción con la API del backend.

3- Despliegue en AWS

EC2: Instancias para ejecutar la aplicación.
Docker: Contenedores para empaquetar y desplegar la aplicación.

## Descripción de la aplicación 📖

Esta aplicación web permite a los usuarios registrar, visualizar, actualizar y eliminar propiedades. Está construida utilizando Spring Boot en el backend y HTML, CSS y JavaScript en el frontend. La aplicación se conecta a una base de datos MySQL para almacenar la información de las propiedades.

Este proyecto proporcionará experiencia práctica en desarrollo full-stack, diseño de APIs REST, gestión de bases de datos, y despliegue en la nube con AWS. 

## Diagrama de Arquitectura ☁️

* Usuario (User):

Es quien realiza solicitudes HTTP a través de un navegador web.
* Navegador (Browser):

Actúa como intermediario entre el usuario y el servidor HTTP.
Realiza solicitudes HTTP al servidor en busca de recursos como archivos HTML, JavaScript, CSS o imágenes.
* Servidor HTTP (HttpServer):

Es el servidor que recibe y procesa las solicitudes HTTP enviadas por el navegador.
Se encuentra dentro de un "grupo genérico", lo que indica que puede formar parte de una infraestructura más amplia.

El navegador envía varias solicitudes HTTP al servidor en el puerto 35000 para diferentes rutas: 🛜

* /script.js: Solicitud para obtener un archivo de JavaScript.
* /index.html: Solicitud para cargar el archivo principal de la página web.
* /estilos.css: Solicitud para cargar el archivo de estilos CSS.
* /Imagen/Chill.jpg: Solicitud para obtener una imagen ubicada en una ruta específica.
* Recursos (Archivos estáticos): Almacenados en el servidor, servidos a través de rutas específicas.
* Comunicación: Protocolo HTTP entre el cliente y el servidor.

El servidor procesa estas solicitudes y responde con los recursos correspondientes desde su sistema de archivos. 🌐

* Servidor HTTP: Clase HttpServer que maneja solicitudes HTTP.
* Manejo de rutas: Clase Route para mapear rutas específicas a manejadores.
* Clases de soporte:
* Request y Response para manejar y estructurar las solicitudes y respuestas.
* Utils con funciones auxiliares
* Archivos estáticos: Recursos en la carpeta resources/Files (HTML, CSS, imágenes, etc.).
* API REST: Endpoints definidos en HttpServer para manejar /api/saludo, /api/fecha, etc.
* Pruebas: Clases de prueba con JUnit para validar el comportamiento del servidor.
  
* Docker: ⌨️
Los servicios están contenedorizados y desplegados en entornos Docker.

* Despliege en la nube: ☁️
La comunicación HTTP final. Aquí es donde los servicios pueden estar alojados en un entorno de cloud computing como AWS

![Diagrama en blanco (2)](https://github.com/user-attachments/assets/c4e1dff5-09ec-4b25-b25d-4d3bd9998acf)

## Diagrama de Clase 💡

Este diagrama de clases representa la estructura del sistema CRUD para gestionar propiedades inmobiliarias utilizando Spring Boot y JPA.

![image](https://github.com/user-attachments/assets/dfffb328-24e9-46d8-91e4-4296849b34de)

## Descripción de las clases

1. Clase Property (Entidad Principal)
Esta clase representa una propiedad inmobiliaria y contiene los siguientes atributos:

id: Long → Identificador único de la propiedad.
address: String → Dirección de la propiedad.
price: String → Precio de la propiedad.
size: String → Tamaño de la propiedad.
description: String → Descripción de la propiedad.
También incluye los métodos getter y setter para manipular los atributos.

2. PropertyController (Controlador REST)
Es el controlador de la API que maneja las operaciones CRUD y expone los endpoints REST.
Contiene los siguientes métodos:

requestMethodName(param: String): String → Un método auxiliar.
createProperty(property: Property): Property → Crea una nueva propiedad.
getAllProperties(): List<Property> → Devuelve una lista con todas las propiedades.
getPropertyById(id: Long): ResponseEntity<Property> → Obtiene una propiedad por su ID.
updateProperty(id: Long, propertyDetails: Property): ResponseEntity<Property> → Actualiza una propiedad existente.
deleteProperty(id: Long): ResponseEntity<Void> → Elimina una propiedad.
Este controlador interactúa con el repositorio PropertyRepository para acceder a la base de datos.

3. PropertyRepository (Interfaz del Repositorio JPA)
Es una interfaz que extiende JpaRepository<Property, Long>.

Permite realizar operaciones sobre la base de datos, como guardar, actualizar, eliminar y buscar propiedades.
Se enlaza directamente con la entidad Property.
4. JpaRepository<Property, Long> (Interfaz Genérica de Spring Data JPA)
JpaRepository<K, V> es una interfaz genérica donde K representa la entidad (Property) y V el tipo de la clave primaria (Long).
Proporciona métodos listos para usar, como save(), findById(), findAll(), deleteById(), entre otros.

5. ResponseEntity<T> (Clase para Manejo de Respuestas HTTP)
Se usa para envolver respuestas HTTP en los métodos del controlador.
ResponseEntity<Property> → Respuesta HTTP con una propiedad como cuerpo.
ResponseEntity<Void> → Respuesta HTTP sin contenido, usada en eliminaciones (DELETE).
Relaciones entre las clases
PropertyController usa PropertyRepository para acceder a los datos.
PropertyRepository extiende JpaRepository<Property, Long>, lo que permite manipular la base de datos sin escribir consultas SQL manuales.
ResponseEntity<T> se utiliza en los métodos del controlador para manejar respuestas HTTP de forma adecuada.

## Comenzando 🚀

Las siguientes instrucciones le permitirán obtener una copia del proyecto en funcionamiento en su máquina local para fines de desarrollo y prueba.

### Tecnologías usadas ⚙️

* [Maven](https://maven.apache.org/) : Gestor de dependencias y automatización de construcción para Java.
* [JavaScript](https://nodejs.org/) : Lenguaje de programación para interactividad en la web.
* [Java](https://www.java.com/es/) : Lenguaje de programación robusto para backend y aplicaciones empresariales.
* [SpringBoot](https://spring.io) : Marco web de Java basado en microservicios de código abierto que ofrece Spring.

```
* Versión Maven: 3.9.9
* Versión Java: 17
```

### Instalación 📦

Realice los siguientes pasos para clonar el proyecto en su máquina local.

```
git clone https://github.com/Pau993/Taller05.git
cd Taller05
git checkout Taller05
mvn clean compile
```

### Ejecutando la aplicación ⚙️

Para ejecutar la aplicación, ejecute el siguiente comando:

```
mvn exec:java -Dexec.mainClass="com.example.Application"

```

El anterior comando limpiará las contrucciones previas, compilará y empaquetará el código en un jar y luego ejecutará la aplicación.

Diríjase a su navegador de preferencia y vaya a la siguiente dirección: [http://localhost:35000/](http://ec2-52-91-91-122.compute-1.amazonaws.com:8080) para ver la aplicación en funcionamiento.

## Ejecutando las pruebas ⚙️

Para ejecutar las pruebas, ejecute el siguiente comando:

Las pruebas realizadas en este proyecto se enfocan en la validación y verificación de requisitos relacionados con el proceso de gestión de solicitudes, asegurando su correcto funcionamiento y cumplimiento de especificaciones.

```
mvn test
```
![image](https://github.com/user-attachments/assets/1140e7e4-0f60-4a51-a479-3919a91e7e20)

## Descripción de las pruebas

1. testCreateProperty (Prueba de Creación de Propiedad)
Descripción:

Simula una solicitud POST a /properties para crear una nueva propiedad.
Envía un JSON con los datos de la propiedad.
Verifica que la respuesta tenga un estado 200 OK.
Valida que los datos de la respuesta sean los mismos que los enviados (dirección, precio, tamaño y descripción).

2. testGetPropertyById (Prueba de Consulta por ID)
Descripción:

Crea y guarda una propiedad en la base de datos usando PropertyRepository.
Simula una solicitud GET a /properties/{id} para recuperar la propiedad creada.
Verifica que la respuesta tenga un estado 200 OK.
Confirma que los datos obtenidos coincidan con los de la propiedad almacenada.

3. testUpdateProperty (Prueba de Actualización de Propiedad)
Descripción:

Crea y guarda una propiedad en la base de datos.
Simula una solicitud PUT a /properties/{id} con nuevos valores para actualizar la propiedad.
Verifica que la respuesta tenga un estado 200 OK.
Confirma que los datos de la propiedad fueron actualizados correctamente en la respuesta.

4. testDeleteProperty (Prueba de Eliminación de Propiedad)
Descripción:

Crea y guarda una propiedad en la base de datos.
Simula una solicitud DELETE a /properties/{id} para eliminar la propiedad.
Verifica que la respuesta tenga un estado 204 No Content, lo que indica que la propiedad fue eliminada con éxito.

## Características principales: ⚙️

1. Interfaz moderna y responsiva:

* Un diseño minimalista con un esquema de colores que incluye degradados de tonos morados, creando una experiencia visual sofisticada.
* Totalmente adaptable a diferentes dispositivos gracias a su diseño responsivo.
* Panel de busqueda de archivos, el cual permite leer cualquier tipo de archivo localmente.
  
2. Gestión de archivos: ⚙️

* Incluye botones interactivos que permiten abrir y visualizar archivos clave como:
* Ver las propiedades
* Agregar propiedades
* Archivos JavaScript (script.js).
* Hojas de estilo CSS (estilos.css).
* Documentos HTML (index.html).
* Imágenes (Chill.jpg).

## Muestra de la aplicación 🧩

https://github.com/user-attachments/assets/53671196-9b61-4c81-a61a-8d86f9b5cca9

## Autores ✒️

* **Paula Natalia Paez Vega* - *Initial work* - [Paulinguis993](https://github.com/Paulinguis993)

## Licencia 📄

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Agradecimientos 🎁

Agradecimientos al profeso Daniel Benavides por brindarme sus conocimientos.
