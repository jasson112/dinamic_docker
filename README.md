# soho_docker
Para la configuracion hacer lo siguiente

1. en el archivo ./apache/docker-compose.yaml y el archivo ./php/docker-compose.yaml 
    - ir a donde dice volume 
        - cambiar ../../flowbusiness_co por la carpeta donde se encuentre flowbusiness
            - ../../flowbusiness_co:/usr/local/apache2/htdocs/flowbusiness_co
        - cambiar ../../cwbusiness.com/core por la carpeta donde se encuentre el core de cwcbusiness
            - ../../cwbusiness.com/core:/usr/local/apache2/htdocs/cwbusiness

Ejecutar los siguientes comandos:

1. para crear la net:
    ``` shell script
    docker network create dinamic_net
    ```
2. para iniciar el mysql:
    ``` shell script
    docker-compose -f ./mysql/docker-compose.yaml up -d
    ```
3. para iniciar el php:
    ``` shell script
    docker-compose -f ./php/docker-compose.yaml up -d
    ```
4. para iniciar el apache:
    ``` shell script
    docker-compose -f ./apache/docker-compose.yaml up -d
    ```
5. Modificar el archivo host y agregar el host para que apunte al puertoi 80 en caso de que sea apache:
    ``` shell script
    https://docs.rackspace.com/support/how-to/modify-your-hosts-file/
    
    #por ejemplo:
    127.0.0.1 devaitek.com
    ```