## Primer Hola Mundo

Realicemos nuestro primer Hola Mundo en Docker utilizando el comando  

  ```
  docker run hello-world
  ```   

## Contenedores
Los contenedores son el **concepto fundamental** al hablar de docker. Un contenedor es una entidad lógica,  
una agrupación de procesos que se ejecutan de forma nativa como cualquier otra aplicación en la máquina host.  

*Un contenedor ejecuta sus procesos de forma nativa*  

## Explorar el estado de docker

Vamos a conocer algunos trucos de nuestra consola para explorar el estado del docker  

Para listar todos los contenedores de Docker, utilizamos el comando :  
 
  ```
  docker ps -a
  ```  
  ## Podemos inspeccionar un contenedor en específico utilizando:  

  ```
  docker inspect nombreDelContenedor
  ```
  ## Para renombrar un contenedor lo hacemos de la siguiente manera  

  ```
  docker rename <nombreContenedorAnterior> <NombreDeContenedorQueQueremos>
  ```
  ## Para borrar un contenedor:  

  ```
  docker rm <NombreDelContenedor> ó <Primeros tres caracteres del ID>
  ``` 

  ## Para ver el output de un contenedor lo hacemos con el siguiente comando

  ```
  docker logs <NombreDelContenedor>
  ```

  ## Con los siguientes parametros podemos ver una lista de containers pero solo nos mostrara sus ID  

  ```
  docker ps -aq
  ```
  ## Para borrar una lista de contenedores hacemos lo siguiente  

  ```
  docker rm $(docker ps -aq)
  ```

  ## Para meternos dentro de un contenedor de manera interactiva

  ```
  docker run -it <Nombre de la imagen>
  ```
  El significado de las flags ***-it***
  ***-t*** Asignar un pseudo-tty (Terminal).
  ***-i*** mantén STDIN abierto incluso si no está conectado.

  ## Para ingresar a la bash de un contenedor de manera interactiva

  ```
  docker exec -it <Nombre contenedor> bash
  ```

  ## Matar procesos

  ```
  docker kill <Nombre contenedor>
  ```

  # Matar el proceso de manera forzada 

  ```
  docker rm -f <Nombre contenedor>
  ```

  ## Correr un servidor con ngnix

  ```
  docker run (--detach) ó (-d) --name nginx
  ```
  Si el contenedor que voy a ejecutar tiene un proceso que tiene output y/o pretende correr en modo interactivo, lo va omitir, me va dar el control de la terminal.

  pero de esta manera solo mantengo el puerto abierto pero dentro del contenedor, para que este puerto escuche desde el navegador 
  hacemos lo siguiente.

  ```
  docker run --detach --name servertwo -p 8080:80 nginx
  ```

  ***-p*** es de publish y esta bandera es para atar los puertos. Primero el de mi maquina y después el del contenedor.
  Ahora en PORTS aparece que puerto de mi maquina está dirigiendo hacia el puerto del contenedor.
  En el navegador localhost:8080 y ya puedo ver nginx, 
  
  el ***8080*** es el puerto de mi host de nuestro servidor y el ***80*** es el puerto del contenedor.

  No puedo asignar más de un contenedor a un mismo puerto.

  ## Crear datos en docker

  ```
  docker run -d --name db -v /Users/rafaellopez/Documents/HTML/CommandDocker/mongodata:/data/db mongo 
  ```

  El ***-v*** es de volumen de datos el siguiente path es el destino de mi pc ***/Users/rafaellopez/Documents/HTML/CommandDocker/mongodata*** despues de los ***:*** es el destino del contenedor que seria el siguiente path ***/data/db mongo ***

  ## Listar volumenes 

  ```
  docker volume ls
  ```
 
  ## Borrar volumenes que no estamos usando en nuestros contenedores

  ```
  docker volume prune
  ```

  ## Crear un volumen

  ```
  docker create volume <Nombre del volumen>
  ```

  Para poder asociar el directorio de un contenedor a un volumen se utiliza el parámetro ***--mount***, luego ***src*** para indicar el volumen donde se guardará la información, y luego ***dst*** para indicar el destino o directorio del contenedor que se montará en el volumen indicado en ***src***

  ```
  docker run -d --name db --mount src=dbdata,dst=/data/db mongo
  ```