En este projecto/práctica de laboratorio, voy a hacer un analisis de una serie de eventos DNS recogidos en un log el cual vamos a analizar en Splunk.

PASOS PREVIOS:
1. Crear un índice "dns_log" .
2. Cargar el log en el apartado Add Data.
3. Asociar el archivo( log) con el índice.

A continuación , para probar que está cargado correctamente usamos index="dns_logs" | head 20 ( muestra los 20 primeros)
![image alt](https://raw.githubusercontent.com/LIGHTZET12/SPLUNK-PROJECTOS/101a63b5532df64c9f8fb54ddb4b43b6dd95c91b/PROJECTO%202.%20DNS/capturas/1.png)



Vamos a centrarnos primero en uno de ellos y vamos a analizarlo poco a poco. 

![image alt](https://github.com/LIGHTZET12/SPLUNK-PROJECTOS/blob/26ca0d1c170245017c9871b8f668e34b856b1ee7/PROJECTO%202.%20DNS/capturas/2.png)

Vemos que la Ip de origen es 192.168.202.122 con el puerto 137, y la IP destino es 192.168.202.255 con puerto 137. Además el protocolo de comunicación utilizado es UDP (TCP/UDP) . El 33707 es el ID de sesión de la consulta DNS. NB se refiere al tipo de consulta realizada y 32 al tamaño del paquete.

Viendo estos datos, vemos que se ha hecho una consulta de alguien de la subred para resolver el nombre NetBIOS y lo hace mediante broadcast en la misma subred para encontrar otros hosts.

Viendo un solo log de forma visual no es tan "coñazo". Pero si cargamos varios logs, al estar los datos contenidos en el _raw, no podemos hacer busquedas particulares como buscar logs por IP de destino, por el puerto fuente, etc... 

Por ello,vamos a usar expresiones regulares para del _raw, crear

