## Conect to Container

Forma de conectarnos a un servicio en docker

´´´sh
open -a Docker
´´´

Inicia los contenedores con Docker Compose
´´´sh
docker-compose up -d
´´´

verifica el estado
´´´sh
docker ps
´´´



Entramos a la base de datos
´´´sh
docker-compose exec mongodb bash
´´´

Una vez dentro, nos conectamos:  terminal aparecera:  root@113a7e5bade0:/# 

podemos ejecutar comandos como:

ls: para ver archivos

## Conect with mongosh

nonectaremos con Mongo Compass (local) por lo tanto buscaremos esa url

´´´sh
mongosh "mongodb://root:root123@localhost:27017/?tls=false"
´´´

o tambien podriamos conectar con mongo atlas (nube):

´´´sh
mongodb+srv://joanadmin:joanadmin123@cluster0.y8ssg.mongodb.net/
´´´

Por cualquiera de las dos conexiones debe aparecer en la terminal:  test> 

# Una vez conectado, podemos ejecutar los siguientes comandos

para mostrar las bases de datos
´´´sh
show dbs
´´´
para conectar con alguna base de datos que muestra el anterior paso
´´´sh
use("platzi_store")
´´´

para mostrar las collecciones
´´´sh
show collections
´´´

realizar consultas
´´´sh
db.products.find()
db.products.find({ name: "product_1"})
db.products.find({ "price": 1200 }).count()
´´´

show collections

