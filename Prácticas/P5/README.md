# PRÁCTICA 5 

## CReplicación de bases de datos MySQL

### Copia Manual
A la hora de realizar una réplica de una base de datos, podemos optar por realizarla de manera manual, esta opción, para situaciones en las que el volumen de datos sea ínfimo, y su constante de cambio también, podría ser una solución. Para ello podríamos realizarlo exportando la base de datos de uno de los servidores e importándola en otro, tal y como se muestra a continuación:  
	 #### Mostramos el contenido de la base de datos... :     
![copiaPorSSH](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/2.PNG)  	   
     #### Primero exportaríamos la base de datos... :      
![copiaPorSSH](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/3.PNG)     
     
     Una vez exportada la base de datos, procederíamos, desde el lado del esclavo, a copiarla al equipo esclavo...:     
![copiaPorSSH](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/5.PNG)      

### Copia Usando Mysqldump
![copiaConMysqlDump](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P5/img/4.PNG)      