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









