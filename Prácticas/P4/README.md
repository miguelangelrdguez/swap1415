# Práctica 4

## Comprobar el rendimiento de servidores web

#### Apache Benchmark
Partimos de la máquina que se usó para la práctica anterior.
Usando esta utilidad (que viene junto a Apache), escribimos:
`ab -n 1000 -c 10 http://www.example.com/test.html`  
y con ello hacemos la batería de pruebas, cuyos valores devueltos se pasan a mostrar gráficamente:    

![apachebenchmark](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P4/img/apache/1-time_taken_for_test.png)    
     
![apachebenchmark](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P4/img/apache/2-failed_request.png)   
     
![apachebenchmark](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P4/img/apache/3-request-per-second.png)     
     
![apachebenchmark](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P4/img/apache/4-time-per-request.png)    
       
Una vez realizada el benchmark con esta herramienta, pasamos a usar Open Web load, ya que httperf nos mostró un incorrecto funcionamiento (puede verse el resultado del benchmark con httperf en [el documento PDF](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P4/pdfs_test/tests.pdf "Resultados Gráficos de los Benchmark") con todos los Benchmark.)     
     
#### Open Web Load     
Usamos la orden    
`siege -b -t 60s 192.168.161.131/prueba.html`    
para poder ejecutar el benchmark, obteniendo los siguientes resultados:    

![apachebenchmark](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P4/img/openWebLoad/1-transactions_per_second.png)    
     
![apachebenchmark](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P4/img/openWebLoad/2-avg_resp_time.png)   
     
![apachebenchmark](https://github.com/miguelangelrdguez/swap1415/blob/master/Pr%C3%A1cticas/P4/img/openWebLoad/3-max_resp_time.png)     
     
#### Siege    
