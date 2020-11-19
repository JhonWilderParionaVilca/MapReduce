# MapReduce
Map Reduce con hadoop y jupiter

## Requisitos

- 🐳 [Docker](https://docs.docker.com/engine/install/debian/)
- 🐳🐳 [Docker compose](https://docs.docker.com/compose/install/)

## USO
- Clonar el repositorio
```sh
$ git clone https://github.com/wilderPariona/MapReduce
$ cd MapReduce
```
Iniciar el docker compose para usar Hadoop
```sh
$ cd cluster-hadoop-docker
$ docker-compose up -d
$ docker ps
```
Se levanta los containers:

**yarnmaster** gestiona el cluster YARN

**namenode** nodo de HDFS(sistema de archivos en hadoop)

4 **datanodes** nodos cluster de datos

- Para usar el ejemplo por defecto de mapreduce de hadoop ejecutamos un a terminal 

```sh
$ docker exec -it namenode bash
# ejecutar dentro de hadoop
$ hadoop jar /usr/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar pi 10 10
```

- uso de Jupiter

Para poder usar de manera sencilla mapearemos las ips de los contenedores en nuestra maquina local

```sh
$ docker inspect namenode | egrep IPAddress
```

cada salida nos dará la IP de nuestros contenedores debemos de configurar el archivo `/etc/host` en nuestra máquina local
```sh
$ sudo vim /etc/hosts
```

En este archivo incluir las ip y el nombre del contenedor al final de lo que esta por defecto(Pulsar i para editar el archivo), usar tab para separar la ip del nombre del container

```sh
172.19.0.7      namenode
172.19.0.5      yarnmaster
172.19.0.6      datanode1
172.19.0.2      datanode2
172.19.0.4      datanode3
172.19.0.3      datanode4

```

Ahora podremos abrir jupiter para usar hadoop: ingresamos a un navegador y tecleamos: `http://namenode:8889/`

Subimos nuestro archivo `MapReduceManualyHadoop.ipynb`

Copiamos el archivo prueba:
```sh
$ cd archivos-prueba 
$ sudo mv APBROBADO.txt /media/notebooks/archivos-prueba/
```

Ejecutar cada instruccion de jupiter(Alt + enter)

## Contributors


## 🤩 Fuentes

[🐙 mincemeatpy](https://github.com/michaelfairley/mincemeatpy)|
[💾 Michael G. Noll](https://www.michael-noll.com/tutorials/writing-an-hadoop-mapreduce-program-in-python/)|
[💻 BLOG DE INFORMÁTICA - UNED](https://informaticaunedblog.wordpress.com/2019/11/11/empieza-a-trabajar-con-tecnologias-big-data-con-hadoop-y-docker/) |
[🐙 cluster-hadoop-docker](https://github.com/accaminero/cluster-hadoop-docker)|
[🐳 Error docker](https://github.com/docker/for-mac/issues/1317#issuecomment-285334588) |

