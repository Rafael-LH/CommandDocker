# Primer Hola Mundo

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

  ## Para meternos dentro de un contenedor 

  ```
  docker run -it <Nombre de la imagen>
  ```
  El significado de las flags ***-it***
  ***-t*** Asignar un pseudo-tty (Terminal).
  ***-i*** mantén STDIN abierto incluso si no está conectado.

  ## Para ingresar a la bash de un contenedor

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
