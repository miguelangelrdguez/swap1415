# PRÁCTICA 5 

## Replicación de bases de datos MySQL

### Copia Manual
A la hora de realizar una réplica de una base de datos, podemos optar por realizarla de manera manual, esta opción, para situaciones en las que el volumen de datos sea ínfimo, y su constante de cambio también, podría ser una solución. Para ello podríamos realizarlo exportando la base de datos de uno de los servidores e importándola en otro.
         
### Copia Usando Mysqldump
	 ##### Mostramos el contenido de la base de datos... :     
![copiaConMysqlDump](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/2.PNG)  	   
     #### Con el fin de asegurarnos que a la hora de realizar la exportación de la base de datos a un fichero .sql usando esta herramienta no se realice ningún cambio, realizamos lo siguiente:      
![copiaConMysqlDump](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/3.PNG)     
     Una vez exportada la base de datos, procederíamos, desde el lado del esclavo, a copiarla al equipo esclavo...:     
![copiaConMysqlDump](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/4.PNG)           
     ... y a importarla:      
![copiaConMysqlDump](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/5.png)      


### Copia Usando Configuración Maestro-Esclavo       
Como el realizar la replicación de la base de datos usando lo anteriormente mencionado es una tarea bastante costosa, se muestra a continuación cómo poder tener replicadas bases de datos de manera instantánea usando una configuración Maestro-Esclavo.      

En primer lugar, editaremos el archivo /etc/mysql/my.cnf en la máquina que actuará como maestro, realizando las siguientes acciones:      
· Comentamos el parámetro bind-address que sirve para que escuche a un servidor: #bind-address 127.0.0.1     
· Le indicamos el archivo donde almacenar el log de errores: log_error = /var/log/mysql/error.log       
· Establecemos el identificador del servidor: server-id = 1       
· Nos aseguramos que exista un registro binario que contendrá toda la información del registro de actualizaciones, primordial para las trasacciones: log_bin = /var/log/mysql/bin.log        

![copiaMaestroEsclavo](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/5_1.PNG)     
![copiaMaestroEsclavo](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/5_2.PNG)     

Una vez hecho esto, guardamos el documento y reiniciamos el servicio: /etc/init.d/mysql restart     

Ahora nos vamos a la máquina esclavo, y editamos el mismo archivo con la consideración de indicar que el server-id será 2     
![copiaMaestroEsclavo](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/5_3.PNG)       

Una vez hecho esto y reiniciado el servicio, desde el lado del maestro, agregamos un usuario que tenga los permisos de acceso para la replicación:     
![copiaMaestroEsclavo](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/7.PNG)    
Y nos fijamos en los datos que necesitaremos para poder completar la configuración:      
![copiaMaestroEsclavo](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/6.PNG)    

Volvemos a la máquina esclava, y le damos los datos del maestro:    
![copiaMaestroEsclavo](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/8.PNG)      
y arrancamos el esclavo:     
![copiaMaestroEsclavo](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/9.PNG)        

para asegurarnos de que todo está bien, podemos comprobar el valor de la variable seconds_behind_master , si este valor es distinto de null (no considerándose 0 como null), todo ha ido bien.
![copiaMaestroEsclavo](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/11.PNG)      
Ya podemos introducir valores en el maestro que veremos al instante reflejados en el esclavo.