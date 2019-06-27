# Primer Hola Mundo

Realicemos nuestro primer Hola Mundo en Docker utilizando el comando   

    ```
    docker run hello-world
    ```

# Contenedores
Los contenedores son el **concepto fundamental** al hablar de docker. Un contenedor es una entidad lógica,  
una agrupación de procesos que se ejecutan de forma nativa como cualquier otra aplicación en la máquina host.  

*Un contenedor ejecuta sus procesos de forma nativa*  

# Explorar el estado de docker

Vamos a conocer algunos trucos de nuestra consola para explorar el estado del docker  

Para listar todos los contenedores de Docker, utilizamos el comando :  
 
  ```
  docker ps -a
  ```  
  Podemos inspeccionar un contenedor en específico utilizando:  

  ```
  docker inspect nombreDelContenedor
  ```