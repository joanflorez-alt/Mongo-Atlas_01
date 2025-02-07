# Mongodb
(cmd shift v)-para ver este doc

Base de datos popular, base de datos Nosql, orientada a documentos

## Tipos de base de datos Nosql

Documentales: empareja cada clave con una estructura de datos compleja que se denomina 'documento', aqui encontramos Mongo

Grafos: se usa para almacenar información sobre redes de datos, como las conexiones sociales, neo4j

clave-valor: son base de datos NoSQL mas simples. redis

orientadas a columnas: Como Cassandra o HBase, permite realizar consultas en grandes base de datos, almacena los datos en columnas en vez de filas.

## Características

facilidad para escalar, hay dos tipos de escalamiento: horizontal y vertical 

vertical: tenemos un servidos o maquina, aqui podemos aumentar las caracteristicas de la maquina para mayor almacenamiento, en estas se puede aumentar el espacio de almacenamiento y memoria ram,

horizontal: es diferente, al tener una de estas maquinas, la copiamos (como nodos), lo que garantiza disponibilidad, sistemas de replicación.

Al analizar ambos tipos de escalamiento tenemos varios tipos de beneficio entre costo y tiempo.

![Tipos de Escalamiento](images/image_1.png)

En la imagen podemos ver que el escalamiento vertial es más facil pero con el tiempo es más costoso.
mientras que con el escalamiento horizontal puede ser mas costoso en el inicio pero luego se mantiene estandar. 

los escalamientos son paradigmas

# Replicas

Las replicas en escalamiento horizontal, permite que si un nodo o replica falla, otra replica pueda realizar la consulta, esto lo llamariamos alta disponibilidad.

![Replicas](images/image_2.png)

Por el contrario en un escalamiento vertival, si se cae el servidor, es la unica maquina, se cae el sistema. 

## DOCUMENTOS

Los documentos son la forma en que Mongo va a almacenar la información que este en un dominio o tener alli, un dominio como productos, inventario de una tienda, clases de un curso, comparten datos que podemos guardarlos en documentos que luego los almacenamos en colecciones.

Document: Una forma de organizar y almacenar información con un conjunto de pares clave- valor o (campo - valor)

# Cómo se ve?

![document](images/image_3.png)

tenemos un documento que se abre con corchetes, en la imagen anterior podria ser la información de un estudiante. el campo - valor se separa por : 

otro ejemplo:

![document](images/image_4.png)

podemos tener sub documentos, por ejemplo en "loc" es un subdocumento o documento anidado con coordenadas, 

# Ejemplo

Una aplicación que queremos que guardelos contactos. en el escalamiento horizontal cada persona puede tener name, age, status y puede ocurrir que otro usuario tenga adicional estatura, lo cual no genera inconveniente con el escalamiento horizontal porque es flexible, el atributo se puede agregar sin mayor complicación, en el escalamiento vertical tendriamos que agregar una columna adicional y en algunos casos, queda vacio. 

Los documents pueden tener campos compartidos y un documento en particular puede tener un atributo adicional. 

## COLECCIONES

Los documents se almacenan en colecciones, los cuales comparten campos entre si. tienen una identidad o un modelo de datos que se relacionan, por ejemplo la colección de productos, en esta podríamos tener muchos documentos, o tambien una colección llamada usuarios que tenga todos los documentos de nuestros usuarios de nuestra aplicación. 

![colection](images/image_5.png)

![comparación](images/image_6.png)



## CREACIÓN PRIMERA BD NoSQL

Implementaremos un servicio en la nube llamado: 

# Mongo Atlas

Mongo atlas ya trae organizado un sistema de clusterización, motor de Mongo y otras características

Modelo de escalamiento - Modelo de replicación

1. Se selecciona Free Cluster el cual es un plan gratuito

![comparación](images/image_7.png)

    Aquí cargaremos un set de datos. 
    Diferentes tipos demodelado y consultas.

2. Entramos a la pagina: mongodb.com

    Entramos a register: Sign in 
    seleccionamos la cuenta para registrarnos, en este caso lo haremos con cuenta gmail

    

    En la parte superior ziquierda aparece la estructura de organización:

    ![comparación](images/image_8.png)

    Seguidamente estan los proyectos, 

    ![comparación](images/image_9.png)

3. Creamos el Cluster, seleccionamos el servidor en la nube, por ejemplo AWS

4. Seleccionamos la region por ejemplo: us-east-1


5. Las credenciales son en este caso:
    username: joanflorez
    password: 95GTDiSVIt6EKiBX

6. Seleccionamos el metodo Atlas

7. En Quickstart,configuramos username: joanadmin, password: joanadmin123 , IP address: 0.0.0.0/0 description: Localhost

    damos crear

    Al entrar en la parte superior izquiera en clusters debe aparecer algo asi:

    ![comparación](images/image_10.png)

    Ya tenemos una base de datos bajo una estructura de organización y una estructura de proyectos (IMPORTANTE)
    Dentro de la organización por ejemplo: PLATZI, hay varios proyectos: Chats, IOT, etc

    En el boton de la derecha con tres puntos al lado de Browse Collections, seleccionamos: (Load Sample Dataset)

    En el siguiente link: 

    [Sample Datasets](https://www.mongodb.com/developer/products/atlas/atlas-sample-datasets/)

8. Ya podemos ver bases de datos en Browse Collections

    ![comparación](images/image_11.png)

    Podemos ver que en Sample_training hay varias colecciones, por ejemplo companies tiene 9500 empresas

    Ya podemos empezar a explorar nuestra primera base de datos. 

## CONSULTAR INFORMACIÓN EN LA BASE DE DATOS

![comparación](images/image_12.png)

Usaremos Mongo Compass, una interfaz visual para hacer consultas y conectarnos a la base de datos. nos sirve para conectarnos a la nube o localmente. 

Entramos a Cluster y damos click en conect:

![comparación](images/image_13.png)

seleccionamos Compass

seleccionamos el sistema opertativo correcto.

instalamosy ejecutamos

seleccionamos el URI del paso 2 para ubicarlo en la conexión en Compass

![comparación](images/image_14.png)

Al copiar la URI debemos escribir el password creado, en este caso: joanadmin123  sin <>
generamos la conexión 

![comparación](images/image_15.png)

Podemos ver las conexiones locales:

![comparación](images/image_16.png)

Le podemos cambiar el nombre desconectando la base de datos y podemos asignarle un color.
guardamos los cambios y volvemos a conectar.

seleccionamos sample_training

![comparación](images/image_17.png)

podemos entrar a la base de datos de trips, aqui podremos visualizar que tiene documentos. 

![comparación](images/image_18.png)

podemos consultar zips que son ciudades con locaciones y población (pop)


9. # Primer Query (consulta)

Este se realiza en compass en formato Json, 

En zips los que son del estado de NewYork

{ state: "NY" }

Arroja 1596 resultados:

![comparación](images/image_19.png)

# Hasta aquí estamos usando Mongo Compass para hacer consultad en Mongo Atlas. 

## MONGO EN VSC

En esta sección realizaremos consultas desde la terminal en vsc, implementando Mongo Query Lenguage.

1. Creamos en la carpeta MONGODB_NOSQL una carpeta o directorio llamodo mongo_intro 
esto lo podemos hacer desde la terminal: mkdir mongo_intro

2. Seguidamente creamos los archivos del repositorio en mongo_intro.

.gitignore

[https://www.toptal.com/developers/gitignore](https://www.toptal.com/developers/gitignore)

En la pagina vamos escribir windows,linux,mac para que ignore este tipo de archivos

![comparación](images/image_20.png)
creamos el codigo, copiamos y pegamos en nuestro .gitignore
esto no va a permitir que suban archivos basura a nuestro repositorio.

.editorconfig

El codigo lo obtendremos del siguiente repositorio:

[https://github.com/platzi/curso-mongodb-intro](https://github.com/platzi/curso-mongodb-intro)

Este codigo es para manejo estandar de espacios, tablas etc en automatico.

# Archivos para generar al extensión desde VSC con Mongo

En la pagina de Mongo, entramos a products

[https://www.mongodb.com/](https://www.mongodb.com/)

![comparación](images/image_21.png)

podemos instalar desde la pagina o directamente desde VSC

![comparación](images/image_22.png)
cmd shift p (para abrir los comandos de mongo)

Es recomendable reiniciar VSC para la correcta instalación de la extensión

3. Iniciamos la conexión. Add Connection

Inicimos la conexión en Connetion String
buscamos la url en Mongo Atlas: Entramos en Mongo en conect -> compass
recuerde introducir el pass: joanadmin123
![comparación](images/image_23.png)

ya esta la conexión!!
![comparación](images/image_24.png)

se puede renombrar el archivo, por ejemplo: Mongo_Atlas

Podemos explorar todos los documentos. 

4. Creamos la carpeta src, y en la carpeta creamos una subcarptea 01_plaground y aqui creamos el archivo query.mongodb

Aqui yya podemos correr codigo de consulta desde la teminal

El codigo que escribamos en query.mongodb se puede ejecutar con el boton play en la parte superior derecha. 

5. Creamos un repositirio para ver nuestras consultas.

Toda la info que en el siguiente repositorio

[https://github.com/platzi/curso-mongodb-intro](https://github.com/platzi/curso-mongodb-intro)

# Dataset:

[https://gist.github.com/nicobytes/fbd8c63977217855ba8afd3e240651c9text](https://gist.github.com/nicobytes/fbd8c63977217855ba8afd3e240651c9)


6. Realizamos la conexión:

git init

git remote add origin git@github.com:joanflorez-alt/Mongo-Atlas_01.git

# primer comit

git add . 

git commit -m "start project"

git rebase --continue

git status

git push origin main --force

# Pasos para actualizar los commits y subir cambios al repositorio remoto

1. Verifica los cambios realizados: git status
2. Añade los cambios al área de preparación (staging area): git add .

    El punto (.) indica que se añadirán todos los archivos modificados o nuevos. Si deseas añadir solo archivos específicos, usa:
        git add nombre_del_archivo

    para agregar todos los cambios:
        git add -A

3. Crea un commit para guardar los cambios Escribe un mensaje claro que describa los cambios realizados:
    git commit -m "Descripción de los cambios realizados"

    

4. Envía los cambios al repositorio remoto Una vez creado el commit, puedes subir los cambios al remoto con:
    git push origin main

Si haces cambios frecuentes, automatiza un flujo más rápido:

1. Añadir y confirmar todo en un solo comando:

    git commit -am "Descripción de los cambios"

    El parámetro -a añade automáticamente todos los archivos modificados (pero no los nuevos).
    Úsalo solo si los archivos nuevos ya han sido añadidos previamente con git add.

2. Empujar directamente después del commit: Si haces cambios frecuentes y quieres combinarlos, puedes usar:

    git push origin main
    
## Instalando Docker

![comparación](images/image_25.png)

[https://docs.docker.com/desktop/setup/install/mac-install/](https://docs.docker.com/desktop/setup/install/mac-install/)

Docker es una herramienta que permite crear, gestionar y ejecutar aplicaciones en contenedores, que son entornos ligeros y portables. Estos contenedores incluyen todo lo necesario para que una aplicación funcione (código, librerías, dependencias), lo que garantiza que se ejecute de la misma manera en cualquier sistema.

¿Para qué sirve Docker?
Estandarización y portabilidad
Puedes empaquetar una aplicación con todas sus dependencias y ejecutarla en cualquier máquina que tenga Docker instalado, independientemente del sistema operativo o configuración.

Aislamiento
Cada contenedor es independiente, lo que evita conflictos entre aplicaciones (por ejemplo, diferentes versiones de Python o bases de datos).

Facilita el desarrollo
Puedes usar imágenes preconfiguradas para desarrollar y probar sin configurar el entorno desde cero.

Despliegue eficiente
Docker es ideal para implementar aplicaciones en producción rápidamente, ya que todo el entorno está definido en el contenedor.

Escalabilidad
Es más fácil escalar aplicaciones dividiéndolas en microservicios, cada uno en su propio contenedor.

Ahorro de recursos
Comparado con las máquinas virtuales, los contenedores son más ligeros y rápidos, ya que comparten el mismo sistema operativo base.

Ejemplo de uso:
Si estás desarrollando una aplicación web, puedes correr un contenedor para la base de datos (MySQL) y otro para la aplicación (Node.js). Todo estará aislado pero podrá comunicarse entre sí.

# Usuario Docker:
joanmf439

## Correr Mongo en Docker y de manera local

Se puede correr cualquier otra base de datos, sin necesidad de drivers de instalación.
La información se guarda en contenedores. facil de eliminar por ejemplo.


# Levantar un contenedor para correr en Mongo.

1. En nuestro proyecto creamos una archivo llamado docker-compose.yml (archivo para especificar cómo se conectan y configuran los contenedores de tu aplicación.)

    En el archivo digitamos el codigo.

documentación para revisar codigo:

[https://hub.docker.com/_/mongo](https://hub.docker.com/_/mongo)

    Debemos crear una carpeta llamada mongo_data para conecta con volumes

          volumes:
            - ./monogo_data:/data/db 

    Esto guarda la info del contenedor

    Esta información tambien se subirá al gitignore para que no suba al repositorio. en .gitignore:

        mongo_data/

2. En la terminal: docker-compose up -d mongodb

    pero antes guardamos el anterior comando en una carpeta en src llamada 02_docker, aqui creamos el archivo docker.md

3. checkeamos: docker-compose ps

    genera los parametros que esta corriendo

4. En Mongo  Compass hacemos una nueva conexión, aqui veremos que URI usa el local host y puerto 27017

    Entramos a advanced connections

    ![comparación](images/image_26.png)

        seleccionamos: mongodb, por ser una conexión local, el otro es para la nube.

    Entramos a Authentication: nuestro usuario: root pass: root123  (esto esta en el archivo docker-compose.yml)

    Entramos a TLS/SSL: Lo seleccionamos en OFF

    Le ponemos nombre a la conexión y elegimos un color: Mongo Docker

5. Una vez conectados podemos ver 3 colecciones: admin, config, local

    podemos crear mas y mas bases de datos.

    ![comparación](images/image_27.png)


    podemos insertar nuevos documentos:

    ![comparación](images/image_28.png)

    ejemplo de documento: insertamos name y price:

    /** 
* Paste one or more documents here
*/
{
  "_id": {
    "$oid": "679909249d8833eebb40d462"
  },
  "name": "product_1",
  "price":1200
}

Quedo guardado en local una base de dato que se llama platzi_store y hemos creado una colección llamada products y agregado un documento. 

6. En VSC tambien podemos hacer la conexión y consultar documentos. 

    para esto necesitamos la url de conexión. para esto desconectamos y entramos a editar:

    ![comparación](images/image_29.png)

tomamos la url: mongodb://root:root123@localhost:27017/?tls=false


Entramos a Mongo desde VSC, damos click en + para hacer una nueva conexión.
seleccionamos conection string y pegamos la url en la parte superior, damos enter y esta la conexión a localhost:27017

le podemos cambiar el nombre a Mongo-docker

7. En la carpeta del proyecto generamos un archivo del query.mongodb y podemos tomar el codigo base del anterior query (Atlas)
    para implementarlo aqui con nuestra base de datos.

    debemos tener presente en cambiar el nombre de la base datos y las colecciones. 

## TERMINAL DIRECTA DE MONGO (Mongosh)

Ya vimos como usar el playground de VSC y Mongo Compass

Nos conectaremos a la base de datos en la nube (Atlas) y tambien nuestra base de datos local.

1. Abriremos una carpeta llamada 03_mongosh para las instrucciones.
    aqui creamos un archivo llamado commands.md
    aqui estaran las instrucciones para entrar a la terminal del contenedor que se esta corriendo.


Hasta este punto ya nos podemos conectar a nuestras bases de datos desde:

Mongo Compass;
El playground de VSC;
Directamente desde la terminal por mongosh 


## JSON vs BSON

Es el formato en el que mongo guarda los documentos, 


# JSON: facil de organizar la información en un documento. facil de leer, formato altamente usado en la industria.

![comparación](images/image_30.png)

Desventaja: 
    - basado en texto, por ende consume mucho espacio.
    - Es limitado, no tiene tantos tipos de datos, unicamente guarda (números, strings, booleans, arrays, otros subdocumento)

Ejemplo de JSON:

![comparación](images/image_31.png)

# BSON: Es una representación binaria de un formato JSON, por lo tanto no consume tanto espacio.

![comparación](images/image_32.png)

![comparación](images/image_33.png)

Ejemplo comparación JSON vs BSON

![comparación](images/image_34.png)


Tipos de datos en BSON:

[https://www.mongodb.com/resources/languages/bson](https://www.mongodb.com/resources/languages/bson)


## Para visualizar entremos a Mongo Compass

Entramos a mongo-docker (recordemos: primero iniciar docker y seguidamente abrirlo desde mongo compass)

Forma de insertar documentos y elegir el tipo de dato.

paso 1:
![comparación](images/image_35.png)

paso 2:
![comparación](images/image_36.png)

paso 3:
![comparación](images/image_37.png)

paso 4:
![comparación](images/image_38.png)


Conclusión, Mongo guarda información BSON en formato JSON.

API MONGO

## OPERACIONES CRUD (Create, Read, Update, Delete)

conectar: db.database
consulta: find()
conteo: count()

ejemplo: db.database.fin().count()

la salida sera la cantidad de documentos

# INSERTANDO UN DOCUMENTO

En este caso trabajaremos con Mongo Atlas (En la nube)
En nuestro playground de VSC

1. Creamos en el proyecto mongo_intro src/04_inset_doc

    En esta carpeta creamos un archivo llamado insert.mongodb

![comparación](images/image_39.png)


Estando en insert.mongodb

2. Creamos una base de datos con el siguiente comando use("platzi_store")

continuar viendo el resto del codigo en el archivo.

3. Al ejecutar el codigo con play aparece el identificador de un solo documento

![comparación](images/image_40.png)

en realidad esta identificando el segundo documento.

4. Creemos un archivo code de consulta, crearemos el archivo: query.mongodb

    revisar codigo del archivo. 

    veremos que aunque en el paso 3, parece un solo identificador, realmente se insertaron los dos documentos, en este monento aparecen 4 documentos, porque se repitieron los dos anteriores, porque se volvio a ejecutar con play el archivo insert.mongodb

5. tambien podemos generar nuestros propios id:


db.products.insertOne({
    _id : 1
    name : "Product_1",
    price : 1000
})

pero se debe tener cuidado para no generar conflicto,
por ejemplo: si volvemos a ejecutar insert.mogodb con nuestro _id : 1 al volver a interstar con play, generará un conflicto porque estariamos ingresando el mismo _id dos veces.

![comparación](images/image_41.png)

# INSERTAR VARIOS DOCUMENTOS 

1. creamos la carpeta 05_insert_many con el archivo: products.mongodb

    revisar el codigo 

2. creamos el archivo query.mongodb para realizar las consultas fuera del archivo que contiene los documentos para poder ver lo que guarda en la nube cuando se generan conflictos en los documentos. 

NOTA: Si un documento genera conflicto, a partir de donde generó el conflicto, de ahi en adelante no dejera guardar mas documentos. (Còmo resolverlo???)


Para esto se crea la instrucción: {odered: false} como otro objeto fuera del array (revisar archivo: products.mongodb)

para verificar que la siguiente instrucción funciona:

    1. crear un _id duplicado en products.mongodb
    2. ejecutar el archivo de consulta query.mongodb

# ACTUALIZAR UN DOCUMENTO updateOne()

Ingresamos a Mongocompas,  y estando en monocompas, conectamos con mongoAtlas, 
entramos a platzi_store veremos los productos que hemos estado creando en los pasos anteriores.

sobre esta interfaz podemos modificar, eliminar, clonar cada documento.

![comparación](images/image_42.png)

Cómo se hacen estos cambios en codigo:

1. creamos la carpeta 06_update_doc, podemos copiar los archivos de 05_insert_many para ubicarlos en la 06.

2. conectamos a mongoatlas

3. corregmimos el archivo products.mongodb quitando el conflicto de repetir _id y ejecutamos play

4. podemos verificar en nuestro archivo query.mongodb que la base de datos ahora tiene los 4 documentos sin conflicto.

# Operadores

![comparación](images/image_44.png)

5. generamos el archivo update_doc_set.mongodb

    ver codigo con operador $set
    este operador sirve para hacer cambios en los atributos y generar nuevos cambios

6. Creamos el archivo update_doc_inc.mongodb

    $inc sirve para incrementar valores.

7. Crearemos el archivo object_id.mongodb

    vamos al archivo products.mongodb y creamos otro documento pero sin id para que mongo genere
    automaticamente el id

![comparación](images/image_43.png)

    se creo el nuevo documento con el id generado automaticamente por mongodb


# ACTUALIZAR VARIOS DOCUMENTOS updateMany()

updateMany()

$set: tambien para crear nuevos atributos

$rename: para renombrar atributos.

$unset: para eliminar atributos

otros operadores

![comparación](images/image_53.png)

En mongocompass vamos a la base de datos training y escogemos la base de datos de zips

![comparación](images/image_45.png)

podemos observar que hay 29470 documentos

Hacemos una consulta: { city : 'CLEVELAND'}

![comparación](images/image_46.png)

mongocompass dice que hay 34 documentos. 
encontramos tambien que la pop es la población, 

Qué pasa si deseamos actualizar todos los 34 documentos que cumplen con esta condición.
por ejemplo deseamos aumentar toda la población en 1000 

1. Creamos la carpeta 07_update_many y en ella el archivo: update_many.mongodb

2. creamos el query.mongodb y organizamos el codigo de consulta en este:

    revisar codigo, queda solo para consultar los documentos

    consultamos la población pop del primer documento es: 2369

3. En update_many.mongodb organizamos el codigo operador para aumentar en 1000 toda la población
    revisar codigo en el archivo. 
![comparación](images/image_47.png)

    vemos que se actualizaron 34 documentos.

4. Consultamos en el query y veremos el cambio en pop, solo del primer documento paso de 2369 a 3369

![comparación](images/image_48.png)

5. El operados $set no solo sirve para actualizar un valor sino tambien para agregar nuevos atributos, crearemos el archivo set.mongodb, en este usamos operador $set
ver codigo del archivo. 

![comparación](images/image_49.png)

veremos que se actualizaron los 34 documentos ahora con el nuevo atributo (consultar en query)

![comparación](images/image_50.png)

6. Renombrar atributos, por ejemplo cambiar el nombre del atributo anterior mynewatrib por newatrib

    ver codigo

7. Consultamos el query y veremos el cambio.

![comparación](images/image_51.png)

8. Ahora eliminaremos atributos con $unset

creamo el archivo unset.mongodb y empleamos el operador para eliminar
al ejecutar veremos que el atributo ya no esta

![comparación](images/image_52.png)

## ARRAY UPDATE operators 

$push (agregar)  $pull (eliminar)

![comparación](images/image_57.png)

Operadores para trabajar con arrays

Dato para trabajar:

[https://gist.github.com/nicobytes/fbd8c63977217855ba8afd3e240651c9](https://gist.github.com/nicobytes/fbd8c63977217855ba8afd3e240651c9)

tomamos Array Update Operators

![comparación](images/image_54.png)

Vamos a crear en platzi store un inventario primeramente vacio (drop()) y luego insertamos varios documentos. en este caso los tags, seran los arrys

Conectamos con el dataset, conectamos con mongo-Atlas

Creamos la carpeta 08_update_arrays

1. Creamos el archivo dataset.mongodb, en este copiamos el codigo de: Array Update Operators y ejecutamos. 

2. creamos el archivo query, el cual llamaremos find.mongodb en este dejamos el codigo de consulta:

    use("platzi_store")
    db.inventory.find()

3. Generamos el archivo para el operador push, push.mongodb

revisar el codigo, el operador push para agregar nuevos elemento en un array


![comparación](images/image_55.png)

luego ejecutamos el find.mongodb veremos que al _id: 4 se agrego un nuevo elemento en el array tags llamado "headphone".

4. Generamos el archivo pull.mongodb, en el manejamos el operador $pull, para eliminar elementos de un array. En este caso ahora eliminaremos el elementos "headphone".

    ejecutamos el archivo de consulta find.mongodb para verificar que efectivamente ya no esta el elemento "headphone" en el _id: 4 en tags.

# ¿Cómo quitar un elemento de todos los arrays en todos los documentos?

5. creamos el archivo pull_many.mongodb en este ejecutaremos el codigo para eliminar un elemento de todos los documentos en el array tags.

ver el codigo. 

antes de ejecutar el codigo, ver el estado actual de los arrays para ver donde esta la palabra "book" la cual vamos a eliminar. "book" esta en 3 documentos de los 5 que hay en total.

![comparación](images/image_56.png)

veremos que al ejecutar se abordaron los 5 documentos pero se hizo el cambio en 3. 

consultamos nuevamente el find.mongodb para verificar que efectivamente ya no esta el elemento "book".

# ¿Cómo quitar varios elementos en una sola instrucción?

$in
6. Creamos el archivo pull_many.mongodb y en este ubicamos el codico de pull.mongodb y lo modificamos agregando el operador $in.

seguidamente corremos el archivo find.mongodb para verificar que efectivamente se borraron varios elementos del array tags en cada documento 














