# Maquina Vulnerable BWAPP

La opcion que escogi es `SQL INJECTION (GET/SELECT)`

![maquina BWAPP ](https://raw.githubusercontent.com/vjp-danielTM/MaquinaVulnerable/refs/heads/main/capturas/1.png)

Cuando hacemos una consulta vemos que en la url sale la consulta que hace

![maquina BWAPP ](https://raw.githubusercontent.com/vjp-danielTM/MaquinaVulnerable/refs/heads/main/capturas/2.png)
Con esto sabemos  dos cosas que el fichero que utiliza es `sqli_2.php` y que haciendo cambios en la url podemos sacar información privada

Por ejemplo voy a sacar la base de datos que utliza cambiando la url
> http://localhost:8001/sqli_2.php?movie=-1 union select 1,database(),3,4,5,6,7 -- &action=go

Con esta parte de la url ?movie=-1 union select 1,database(),3,4,5,6,7 -- &action=go

UNION SELECT 1, database(), 3, 4, 5, 6, 7 → Añade una fila falsa con estos valores exactos.

database() → es una función de MySQL que devuelve el nombre de la base de datos actual.

![maquina BWAPP ](https://raw.githubusercontent.com/vjp-danielTM/MaquinaVulnerable/refs/heads/main/capturas/3.png)

--- 

Ahora vamos a comprobar que funcione en los otros niveles
![maquina BWAPP ](https://raw.githubusercontent.com/vjp-danielTM/MaquinaVulnerable/refs/heads/main/capturas/4.png)
Vemos que con el nivel medium si funciona

![maquina BWAPP ](https://raw.githubusercontent.com/vjp-danielTM/MaquinaVulnerable/refs/heads/main/capturas/5.png)
Pero vemos que en el nivel high no

---
Vamos a ver el porque, gracias a la url sabemos que sqli_2.php es el fichero que utiliza.
Desde dentro del contenedor hacemos un cat a sqli_2.php y buscamos donde esta el posible fallo 
Este cacho de codigo PHP es un fallo de seguridad porque recoge el parámetro movie de la URL con $_GET["movie"], lo concatena en la consulta SQL mediante $sql .= " WHERE id = " . sqli($id), por lo que el valor del usuario entra dentro de la query. La consulta final queda como SELECT * FROM movies WHERE id = (lo que quiera poner dentro de la url), permitiendo que un atacante envíe consultas como 1' OR '1'='1 -- o -1 UNION SELECT ... -- para devolver todos los registros, extraer datos sensible, modificar o borrar información de la base de datos si el usuario tiene los permisos suficientes
![maquina BWAPP ](https://raw.githubusercontent.com/vjp-danielTM/MaquinaVulnerable/refs/heads/main/capturas/6.png)

Aqui podemos ver la funcion de los checks que hace en la consulta


![maquina BWAPP ](https://raw.githubusercontent.com/vjp-danielTM/MaquinaVulnerable/refs/heads/main/capturas/7.png)

Si seguimos subiendo podemos ver los archivos que incluye el fichero y el de functions es el que suena mas convincente para tener los checks donde tenemos `no_check` y `sqli_check_2`.


![maquina BWAPP ](https://raw.githubusercontent.com/vjp-danielTM/MaquinaVulnerable/refs/heads/main/capturas/8.png)


Si buscamos podemos ver que el no_check lo que hace es retornar la data sin ver nada, es decir no hace nada.

![maquina BWAPP ](https://raw.githubusercontent.com/vjp-danielTM/MaquinaVulnerable/refs/heads/main/capturas/9.png)

Y en sqli_check_2 lo que hace con el `mysql_real_escape_string` escapa caracteres especiales que podrían romper o alterar una consulta SQL

![maquina BWAPP ](https://raw.githubusercontent.com/vjp-danielTM/MaquinaVulnerable/refs/heads/main/capturas/10.png)

#### Autor

> **_Daniel Trujillo Martin_**