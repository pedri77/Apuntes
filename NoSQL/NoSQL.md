# Curso de NoSQL<!-- omit in toc -->

## Índice<!-- omit in toc -->

- [¿Qué es NoSQL?](#que-es-NoSQL)
- [Conceptos en bases de datos no relacionales](conceptos-en-bases-de-datos-no-relacionales)
- [Ventajas y desventajas de NoSQL](#ventajas-y-desventajas-de-NoSQL)
    - [Ventajas de NoSQL](#ventajas)
    - [Desventajas de NoSQL](#desventajas)
- [Diferencias con SQL](#diferencias-con-SQL)
    - [Diferencias entre SQL y NoSQL](#diferencias-entre-SQL-y-NoSQL)
    - [Los principios fundamentales de un sistema de datos distribuido son](#los-principios-fundamentales-de-un-sistema-de-datos-distribuido-son)
- [Modelado de datos en MongoDB relaciones uno a uno y uno a muchos](#modelado-de-datos-en-MongoDB-relaciones-uno-a-uno-y-uno-a-muchos)
- [Tipos de bases de datos NoSQL](#tipos-de-bases-de-datos-NoSQL)
- [Ejecución de código JS en la shell de MongoDB](#ejecución-de-código-JS-en-la-shell-de-MongoDB)
    - [Comandos](#comandos)
    - [Operaciones CRUD en MongoDB](#operaciones-CRUD-en-MongoDB)
- [Enlaces de Interés](#enlaces-de-interés)

## ¿Que es NoSQL?

Not only SQL es una clase de motor base de datos que puede o no seguir todas las reglas de una base de datos relacional, y puede o no usar SQL.

![NoSQL](/NoSQL/DBaaS-and-four-types-of-NoSQL-Databases-you-should-learn-now.gif)

En la actualidad surgen nuevos desafíos en relación a las bases de datos. Las bases de datos relacionales no fueron diseñadas para hacer frente a los desafíos de escala y agilidad que enfrentan las aplicaciones modernas, ni tampoco fueron construidas para aprovechar el poder de almacenamiento y procesamiento de productos disponibles en la actualidad.

- MongoDB resuelve un problema de escalabilidad.
- Redis nos resuelve el problema de guardar información con llave - valor.

Una definición desde un proveedor

[Nosql](https://aws.amazon.com/es/nosql/)

"Las bases de datos NoSQL utilizan una variedad de modelos de datos para acceder y administrar datos, como documentos, gráficos, clave-valor, en-memoria y búsqueda. Estos tipos de bases de datos están optimizados específicamente para aplicaciones que requieren grandes volúmenes de datos, baja latencia y modelos de datos flexibles, lo que se logra mediante la flexibilización de algunas de las restricciones de coherencia de datos en otras bases de datos".

## Conceptos en bases de datos no relacionales

- Full Page Cache

Redis y Memcache son dos bases de datos NoSQL muy utilizadas a la hora de aplicar la técnica de Full Page Cache para disminuir el tiempo de carga y el consumo de recursos en un aplicación web. Full Page Cache consiste en renderizar una página web y guardar el HTML en una base de datos, para que cuando otros usuarios soliciten el recurso pueda ser respondido casi de inmediato sin necesidad de hacer nuevamente un render de la página.

Esta aplicación está muy extendida y es importante en muchos tipos de aplicaciones acudir a una base de datos NoSQL para implementarla.

- Query caching

Algunas veces no es posible realizar cache de todo el HTML de una página web, en esos casos se pueden implementar otra técnica como Query Caching.

Consiste en almacenar el resultado de una consulta a la base de datos, de esta manera si en el futuro se requiere la misma información se puede consultar rápidamente sin necesidad de hacer la consulta completa. 

Los motores de bases de datos como MySQL y Postgres ofrecen esta funcionalidad, pero con Redis también se podría hacer y obtener mejores resultados si tu aplicación es bastante concurrida.

- Leaderboard

Es común en juegos crear una tabla de clasificación de jugadores con sus puntos para clasificación en un juego como League of Legends, Dota, Heroes of the Storm, Counter Strike. Estos juegos en línea y tiempo real requieren que los puntos estén actualizados y que la latencia de escritura y lectura sea baja.

Redis ofrece esta posibilidad con ZADD, este tipo de datos es perfecto para implementar un sistema de clasificación en un juego e incluso para implementar gamification en tu aplicación.

- Multipropositos

Si deseas hacer una aplicación podrías usar NoSQL para cualquier cosa. MongoDB tiene el propósito de servir bajo cualquier circunstancia, es importante tener en cuenta qué podría necesitar tu software en el futuro y de esta manera poder complementar Mongo con algún otro motor de base de datos no relacional o con una base de datos SQL.

## Ventajas y desventajas de NoSQL

### Ventajas

- Escalabilidad: Es la forma en la que la base de datos se expande a la hora de almacenar información, las bases de datos NoSQL están diseñadas para escalar fácilmente de manera horizontal, generando beneficios como alta disponibilidad.

![Escalabilidad](/NoSQL/Escalabilidad.png)

- Esquemas de bases de datos flexibles: Podrías guardar diferentes tipos de información bajo la misma tabla, diferentes registros con diferentes campos en la misma colección.

- Velocidad: Las bases de datos pueden ser muy rápidas con respecto a las bases de datos SQL, un error común es tratar de que una base de datos NoSQL funcione como una base de datos relacional, mientras uses el motor de bases de datos para su propósito inicial vas a obtener las mejores características del motor.

### Desventajas

- No son transaccionales: Las transacciones son consultas generalmente de escritura, donde si ocurre un error, se hace rollback a todo lo que se hizo en la base de datos. NoSQL no garantiza que eso suceda, es desventaja si tu aplicación requiere que la información se guarde completa y se requiere volver a estados anteriores.

- No tiene joins: Porque de hecho no tiene relaciones. Con MongoDB muchas personas tratan de simular relaciones con los índices pero en ese punto Mongo pierde sentido, si estás usando una base de datos NoSQL debes evitar usar joins.

# Diferencias con SQL

## Diferencias entre SQL y NoSQL:

SQL es el lenguaje de programación que utilizan la mayoría de los sistemas, está basado en álgebra relacional. En una base de datos NoSQL no estamos obligados, incluso muchas veces el motor no implementa el lenguaje.

Las bases de datos NoSQL están diseñadas para ser distribuidas desde el comienzo, las bases de datos relacionales no.

Sharding: Con las bases de datos NoSQL puedo tener varios servidores y en cada servidor tener una parte de la base de datos, puedo distribuir la información y eso me facilita los procesos de recuperación y puedo escalar únicamente lo que necesito y no es necesario escalar todo el cluster. En las bases de datos relacionales es complejo el proceso de distribución.

## Los principios fundamentales de un sistema de datos distribuido son:

- Autonomía local.
- No dependencia de un sitio central.
- Operación continúa.
- Independencia con respecto a la localización.
- Independencia con respecto a la fragmentación.
- Independencia de réplica.
- Procesamiento distribuido de consultas.
- Manejo distribuido de transacciones.
- Independencia con respecto al equipo.
- Independencia con respecto al sistema operativo.
- Independencia con respecto a la red.
- Independencia con respecto al SGBD.

# MongoDB

MongoDB puede usarse con muchos lenguaje de programación, [aquí](https://docs.mongodb.com/manual/applications/drivers/) puedes consultar los drivers oficiales disponibles.

![MongoDB](/NoSQL/SQL-MongoDB- Correspondence.png)

### Definición

MongoDB es una base de datos NoSQL de tipo documental. Es una base de datos no relacional que nació en el 2007, está programada en c++. 
Es una base de datos documental, significa que se almacena la información en documentos, es decir en formato json, se almacena en bson que son json pero binarios.
Permite crear aplicaciones ágiles y escalables. 
Esta base de datos ha sido creada para brindar escalabilidad, rendimiento y gran disponibilidad, escalando así de una implementación único (escalado vertical) a grandes arquitecturas complejas de centros multidatos (escalado horizontal).

-el equivalente a las filas de una base de datos SQL serian los documentos, los cuales se guardan en formato BSON, lo cual es un archivo en json almacenado de forma binaria.

Finalmente las columnas son representadas por campos, estos campo son flexibles y podemos guardar cualquier información sin necesidad de tener especificado el tipo de información a guardarse en el campo

Resumen:

Database ->	Database
Tables ->	Coleccions
Rows	->	Documents (BSON)
Colums	->	Fields

## Modelado de datos en MongoDB relaciones uno a uno y uno a muchos

- En mongo DB un documento se puede conformar con al menos un campo(_id) este es un campo obligatorio que es autogenerado por la DB
- Podemos crear Sub-documentos agregando un json en lugar de un campo
- Podemos hacer referencia a otros documentos y con esto emular algo similar a lo que serian las relaciones en sql
- Es aceptado redundar información en bases de datos NoSql

![Modelado](/NoSQL/im_01.png)

![Modelado Uno a uno](/NoSQL/im_02.png)

![Modelado de árbol](/NoSQL/im_03.png)

Referenciando al padre:
![Referenciando al padre](/NoSQL/Referencia_al_padre.png)
Referenciando al hijo:
![Referenciando al hijo](/NoSQL/Referencia_al_hijo.png)

# Tipos de bases de datos NoSQL

- Clave-valor: las bases de datos clave-valor son altamente divisibles y permiten escalado horizontal a escalas que otros tipos de bases de datos no pueden alcanzar. Los casos de uso como juegos, tecnología publicitaria e IoT se prestan particularmente bien con el modelo de datos clave-valor. Amazon DynamoDB está diseñado para proporcionar una latencia de milisegundos constate de un solo dígito para cualquier escala de cargas de trabajo. Este desempeño coherente responde en gran parte por qué la función de historias de Snapchat, (que incluye la carga de trabajo del escritura de almacenamiento más grande de Snapchat) se trasladó a DynamoDB.
nosql_document_g

- Documento: algunos desarrolladores no piensan en su modelo de datos en términos de filas y columnas desnormalizadas. Normalmente, en el nivel de aplicación, los datos se representan como un documento JSON porque es más intuitivo para los desarrolladores pensar en su modelo de datos como un documento. La popularidad de las bases de datos de documentos ha crecido porque los desarrolladores pueden conservar los datos en una base de datos utilizando el mismo formato de modelo de documentos que usan en su código de aplicación. DynamoDB y MongoDB son bases de datos de documentos muy conocidas que proporcionan API poderosas e intuitivas para un desarrollo flexible y ágil.
nosql_graph_g

- Gráfico: el propósito de una base de datos de gráficos es facilitar la creación y la ejecución de aplicaciones que funcionan con conjuntos de datos altamente conectados. Los casos de uso típicos para una base de datos de gráficos incluyen redes sociales, motores de recomendaciones, detección de fraude y gráficos de conocimiento. Amazon Neptune es un servicio de base de datos de gráficos completamente administrado. Neptune admite tanto el modelo de Property Graph como el Resource Description Framework (RDF), que ofrece la opción de dos API de gráficos: TinkerPop y RDF/SPARQL. Las bases de datos de gráficos populares incluyen Neo4j y Giraph.
nosql_inmemory_g
- En-memoria: las aplicaciones de juegos y tecnología publicitaria tienen casos de uso como tablas de clasificación, tiendas de sesión y análisis en tiempo real que requieren tiempos de respuesta de microsegundos y pueden tener grandes picos de tráfico en cualquier momento. Amazon ElastiCache ofrece Memcached y Redis, para servir cargas de trabajo de baja latencia y alto rendimiento, como McDonald’s, en las que no se pueden servirse con almacenes de datos basados en disco. Amazon DynamoDB Accelerator (DAX) es otro ejemplo de un almacén de datos especialmente diseñado. DAX hace que DynamoDB lea una orden de magnitud más rápida.
nosql_search_g
- Buscar: muchas aplicaciones generan registros para ayudar a los desarrolladores a solucionar problemas. Amazon Elasticsearch Service (Amazon ES) está diseñado para proporcionar visualizaciones en tiempo real y análisis de datos generados por máquinas al indexar, agregar y buscar registros y métricas semiestructuradas. Amazon ES también es un poderoso motor de búsqueda de alto desempeño para casos de uso de búsqueda de texto completo. Expedia está utilizando más de 150 dominios de Amazon ES, 30 TB de datos y 30 mil millones de documentos para una variedad de casos de uso críticos, que van desde la monitorización operativa y la resolución de problemas, hasta el seguimiento de la pila de aplicaciones distribuidas y la optimización de precios.

# Ejecución de código JS en la shell de MongoDB

MongoDB ha crecido rápidamente hasta convertirse en una popular base de datos para aplicaciones web y es un complemento perfecto para las aplicaciones NodeJS, permitiéndole escribir JavaScript para el cliente, backend y la capa de base de datos.

### Comandos

<code>$ mongo --help</code> Muestra el menú de ayuda.
<code>$ show dbs</code> Muestra las bases de datos existentes en MongoDB.
<code>$ use [name-db]</code> Permite usar una base de datos determinada.
<code>$ db.collection.insert({JSON-Document})</code> Permite crear una colección (tabla en MySQL) e insertar datos en una base de datos.
</code>$ show collections</code> Muestra las colecciones existentes.
<code>$ db.createCollection('name-colletion')</code> Crea una colección de manera explicita.
<code>$ load('name-file.js')</code> Permite cargar un archivo JavaScript a MongoDB.

### Operaciones CRUD en MongoDB

- Insertar documentos desde la consola de Mongo

El CRUD describe las funciones elementales de una base de datos persistente. 

#### CRUD significa Crear, Recuperar/Leer, Actualizar y Eliminar.

Operaciones de crear e insertar nuevos documentos a una colección. Si la colección no existe actualmente, las operaciones de inserción crearán la colección.

MongoDB proporciona los siguientes métodos para insertar documentos en una colección:

<code>db.collection.insert({JSON-Document})</code> Permite agregar una o varias colecciones a una base de datos.
<code>db.collection.insertOne({JSON-Document})</code> A diferencia del insert({JSON-Document}), este método solo inserta una colección.
<code>db.collection.insertMany([{JSON-Document}, {Other-JSON-Document}, {...}]) </code>Este método es similar a insert({JSON-Document}), sin embargo, este método fue incluido en la versión 3 de MongoDB por ende debe comenzar a usarse y evitar insert({JSON-Document}).

- Funciones find y findOne
Las operaciones de lectura, recuperan documentos de una colección. MongoDB proporciona los siguientes métodos para leer documentos de una colección:

<code>db.collection.find()</code> Imprime los primeros 20 documentos que encuentra.
<code>.limit(n)</code> Imprime los primeros n documentos que encuentra.
<code>.pretty()</code> Imprime los documentos de una forma más legible.
<code>db.collection.find({"clave": "valor"}, {"clave": valor})</code> Imprime el documento que contenga la(s) clave(s) y el (o los) valor(es) especificado(s). 
<code>Con findOne({...})</code> se muestran los documentos de forma más legibles para la vista.
<code>db.collection.find({"clave": {$gt: "valor"}})</code> Imprime los documentos mayores al valor de alguna clave en un documento.
<code>$gt </code>Significa mayor que (>).
<code>$lt </code> Significa menor que (<).
<code>$gte </code> Significa mayor o igual a (>=).
<code>$lte </code> Significa menor o igual a (<=).
<code>db.collection.findOne() </code> Imprime solo el primer documentos que encuentra.
- Modificación de documentos en la consola de MongoDB

Las operaciones de actualización, modifican los documentos existentes en una colección. MongoDB proporciona los siguientes métodos para actualizar documentos de una colección:

<code>db.collection.save({JSON-Document)}</code> Modifica un campo si se encuentra en una colección, si no se agrega.
<code>db.collection.update({JSON-Document)}</code> Actualiza el documento por completo, es decir, elimina todos los campos y agrega los nuevos dejando así solo el _id.
<code>db.collection.updateOne({filtro}, {"clave": "valor"})</code> Se actualizará el primer documento que coincida con el filtro.
<code>db.collection.updateMany({filtro}, {"clave": "valor"})</code> Se actualizará todos los documentos que coincida con el filtro.

- Eliminar documentos en la consola de MongoDB

Las operaciones de borrado, eliminan documentos de una colección. MongoDB proporciona los siguientes métodos para eliminar documentos de una colección:

<code>db.collection.deleteOne({"filter")}</code> Elimina el primer documento encontrado según el filtro.
<code>db.collection.deleteMany({"filter")}</code> Elimina todos los documentos encontrados según el filtro.
<code>db.collection.remove({"filter")}</code> Elimina un campo según el filtro, es decir, si coincide uno o muchos documentos con el filtro serán eliminados de la base de datos.
<code>db.collection.drop()</code> Elimina todos los documentos de una colección.

# ¿Qué es Redis?
Redis es un almacén de estructura de datos en memoria de código abierto (con licencia de BSD), que se utiliza como base de datos, caché y agente de mensajes.

![Redis](/NoSQL/Redis_Logo.png)

Admite estructuras de datos tales como cadenas, hashes, listas, conjuntos, conjuntos ordenados con consultas de rango, mapas de bits, hiperlogálogos e índices geoespaciales con consultas radiales. Redis tiene una replicación incorporada, secuencias de comandos Lua, desalojo LRU, transacciones y diferentes niveles de persistencia en disco, y proporciona alta disponibilidad a través de Redis Sentinel y particiones automáticas con Redis Cluster.

Redis corre por defecto en el puerto 6379.

- Comandos Redis

<code>redis-cli --help </code>Muestra el menú de ayuda.
<code>SELECT [number-db]</code> Cambia de base de datos. Redis por defecto tiene 16 DBs configuradas.
<code>SET [clave] [valor]</code> Inserta un campo y este mismo se almacena como un string.
<code>DEL [clave] </code>Elimina un campo por medio de su clave de identificación.


## Enlaces de Interés

* [Curso MongoDB y Redis](https://platzi.com/cursos/mongodb-redis/)
* [ZADD](https://redis.io/commands/zadd)
* [BSON](https://es.wikipedia.org/wiki/BSON)
* [Docu oficial MOngoDB](https://docs.mongodb.com/manual/tutorial/)
* [Comandos MongoDB](https://docs.mongodb.com/manual/reference/command/#database-operations)
