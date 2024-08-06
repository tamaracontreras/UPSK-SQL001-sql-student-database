# Learn SQL by Building a Student Database: Part 2

### Lo primero que necesitas hacer es iniciar el terminal.
Hazlo haciendo clic en el menú "hamburguesa" en la parte superior izquierda de la pantalla, yendo a la sección "terminal" y haciendo clic en "nuevo terminal". Una vez que abras uno nuevo, escribe echo hello SQL en el terminal y presiona enter.
*echo hello SQL

### En la Parte 1 de este tutorial, creaste una base de datos de estudiantes y luego un script para insertar información sobre tus estudiantes de ciencias de la computación en ella. Inicia sesión en el terminal interactivo de psql con psql --username=freecodecamp --dbname=postgres para ver si está ahí.
* psql --username=freecodecamp --dbname=postgres

Lista las bases de datos:
*\l

### Tu base de datos no está aquí. Puedes usar el archivo .sql que creaste al final de la Parte 1 para reconstruirla. Recomiendo "dividir" el terminal. Puedes hacerlo haciendo clic en el menú "hamburguesa" en la parte superior izquierda de la ventana, yendo al menú "Terminal" y haciendo clic en "Dividir Terminal". Una vez que lo hayas hecho, ingresa psql -U postgres < students.sql en él para reconstruir la base de datos.
* psql -U postgres < students.sql en terminal bash

### Han ocurrido muchas cosas en la terminal. Parece prometedor. En el indicador de psql, vuelva a ver las bases de datos.

* \l en la terminarl de psql
Allí está la base de datos de tus alumnos. Conéctate a ella.
* \c students

### Ahora que está conectado, visualice las tablas y relaciones que se encuentran aquí para ver si todo está correcto.
* \d

### Todo parece correcto. Observa los detalles de la tabla de estudiantes para asegurarte de que la estructura sea correcta.
* \d students

### Se ve bien. Asegúrate de que todos los datos estén en la tabla también.
* SELECT * FROM students;

### Los datos están todos ahí. Debes echar un vistazo a los detalles de las otras tablas y los datos que contienen para asegurarte de que se ven bien. Cuando hayas terminado, usa touch en la terminal bash para crear student_info.sh. Vas a crear un script para imprimir información sobre tus estudiantes.
* touch student_info.sh

### Otorgue a su nuevo archivo permisos de ejecución.
* chmod +x student_info.sh

### Agrega un shebang que usa bash en la parte superior de tu nuevo script.

* #!/bin/bash

### Debajo del tema, agregue un comentario que diga Información sobre mis estudiantes de informática de la base de datos de estudiantes.

* #Info about my computer science students from students database

### En el nuevo script, use echo para imprimir ~~ My Computer Science Students ~~. Use el indicador -e para colocar una nueva línea al principio y al final del texto.

* echo -e "\n~~ My Computer Science Students ~~\n"

* echo -e "\\n~~ My Computer Science Students ~~\\n"
*  utiliza el comando echo con la opción -e para habilitar la interpretación de las secuencias de escape. Esto permite agregar nuevas líneas antes y después del texto "~~ My Computer Science Students ~~", creando un encabezado visualmente separado en la salida del script.  

### Ejecuta el script: **./nombredelarchivo**
* ./student_info.sh

### Deberás consultar la base de datos nuevamente para obtener información sobre los estudiantes que se mostrarán. Agrega la misma variable PSQL que utilizas en tu script insert_data.sh. Se vería así: **PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"**

* insertar en la parte inferior del script :
* PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"

### Debajo de la variable PSQL que acaba de agregar, use echo para imprimir el nombre, apellido y GPA de los estudiantes con un GPA de 4.0:. Use el indicador -e para colocar una nueva línea al comienzo de la oración.

* insertar en la parte inferior del script : 
* echo -e "\nFirst name, last name, and GPA of students with a 4.0 GPA:"

### Querrá imprimir lo que solicita esa oración. Debe saber cómo realizar esa consulta, pero practiquemos un poco primero. SQL significa "lenguaje de consulta estructurado". Es el lenguaje que ha estado utilizando para administrar sus bases de datos relacionales. En el indicador psql, visualice todos los datos en la tabla de estudiantes como lo ha hecho muchas veces.
* SELECT * FROM students;

### Debes mirar los títulos de las columnas que se devolvieron. El * obtiene todas las columnas de una tabla con tu consulta. Puedes devolver columnas específicas si colocas el nombre de la columna en la consulta en lugar de *. En el indicador de psql, visualiza solo la columna first_name de la tabla students.
* SELECT first_name FROM students;

### En ese momento, solo se devolvió la columna first_name. Puede especificar tantas columnas como desee separándolas con comas. Vea las columnas first_name, last_name y gpa de la tabla students.
* SELECT first_name, last_name, gpa FROM students;

### Puede devolver solo las filas que desee agregando WHERE <condition> a su consulta. Una condición puede constar de una columna, un operador y un valor. Use uno de estos para ver las mismas columnas que antes, pero solo las filas WHERE gpa < 2.5.

* SELECT first_name, last_name, gpa FROM students WHERE gpa < 2.5;

### El operador < solo muestra filas en las que la columna de promedio de calificaciones fue menor a 2,5. Otros operadores son: <, >, <=, >=. Muestra las mismas columnas, pero solo las filas de los estudiantes con un promedio de calificaciones mayor o igual a 3,8.
* SELECT first_name, last_name, gpa FROM students WHERE gpa >= 3.8;

### Eso solo arrojó estudiantes con un promedio de calificaciones de 3.8 o más. También hay operadores de igualdad (=) y desigualdad (!=). Vea las mismas columnas para los estudiantes que no tienen un promedio de calificaciones de 4.0.
* SELECT first_name, last_name, gpa FROM students WHERE gpa != 4.0;

### La consulta correcta le proporcionará únicamente los datos que está buscando. De vuelta en el archivo student_info.sh, agregue un comando echo al final que imprima lo que solicita la oración anterior. Coloque comillas dobles alrededor de él de esta manera: echo "$($PSQL "<query_here>")". Esto hará que el resultado no esté todo en una sola línea.

* echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE gpa = 4.0")"
```
en esta parte se me cerro el tutorial, y cuando fui a correr el archivo no estaba ...

de la siguiente forma lo recupere por bash

camper: /project$ ./student_info.sh
bash: ./student_info.sh: No such file or directory
camper: /
camper: /
camper: /project$ find /workspace -name student_info.sh
/workspace/project/.freeCodeCamp/reset_files/student_info.sh
camper: /project$ cp /workspace/project/.freeCodeCamp/reset_files/student_info.sh /workspace/project/
camper: /project$ ls
student_info.sh
```

luego de eso Ejectuté el archivo: ./student_info.sh:
```
~~ My Computer Science Students ~~


First name, last name, and GPA of students with a 4.0 GPA:
Casares|Hijo|4.0
Vanya|Hassanah|4.0
Dejon|Howell|4.0
```
### Agregue otra declaración echo al final del script. Haga que imprima todos los nombres de los cursos cuya primera letra esté antes de la "D" en el alfabeto:. Coloque una nueva línea delante de ella como en la primera oración.
* echo -e "\nAll course names whose first letter is before 'D' in the alphabet:"

### Primero practique. En el indicador psql, visualice todos los datos de la tabla de especialidades.(majors)
*SELECT * FROM majors;

### Los operadores que usaste con números en la última sección también se pueden usar con texto. Usa el signo = para ver todas las carreras que se llaman Game Design. No olvides que debes usar comillas simples alrededor de los valores de texto.
*SELECT * FROM majors WHERE major = 'Game Design';

### A continuación, vea todas las filas que no sean iguales a 'Game Design'
* SELECT * FROM majors WHERE major != 'Game Design';

### Utilice el operador mayor que para ver las letras mayores que vienen después en orden alfabético.
* SELECT * FROM majors WHERE major > 'Game Design';
 
###  'Game Design' no se incluyó en los resultados porque no es mayor: > 'Game Design'. Inténtalo con el operador mayor o igual a.
* SELECT * FROM majors WHERE major >= 'Game Design';

### En esa ocasión, se incluyó 'Game Design' en los resultados. Por lo tanto, si desea ver los resultados que comienzan con G o después, puede usar la letra mayor >= 'G'. Vea las letras mayores que aparecen antes de G.
* SELECT * FROM majors WHERE major < 'G';

### En el script, agrega un eco en la parte inferior para imprimir la información sugerida como lo hiciste antes. Asegúrate de usar comillas dobles donde sea necesario.
* echo "$($PSQL "SELECT course FROM courses WHERE course < 'D'")"

### Ejecuta el script :
* ./student_info.sh

```
~~ My Computer Science Students ~~

First name, last name, and GPA of students with a 4.0 GPA:
Casares|Hijo|4.0
Vanya|Hassanah|4.0
Dejon|Howell|4.0

All course names whose first letter is before 'D' in the alphabet:
Computer Networks
Computer Systems
Artificial Intelligence
Calculus
Algorithms
```

### Parece que hay cinco. Agregue otra oración como las demás que dice: Nombre, apellido y GPA de los estudiantes cuyo apellido comienza con una "R" o después y tienen un GPA mayor a 3.8 o menor a 2.0:

* echo -e "\nFirst name, last name, and GPA of students whose last name begins with an 'R' or after and have a GPA greater than 3.8 or less than 2.0:"

### Para encontrar eso, comienza usando el prompt de psql para ver todos los datos en la tabla de estudiantes.
* SELECT * FROM students;

### Devolvió 31 filas. Usa el mismo comando, pero solo devuelve las filas para los estudiantes cuyo apellido viene antes de la letra M en el alfabeto.

*SELECT * FROM students WHERE last_name < 'M';

### Eso devolvió 18 filas. Puedes usar múltiples condiciones después de WHERE con AND u OR, entre otros. Solo añade la palabra clave y otra condición. En el prompt de psql, usa el mismo comando que antes, pero añade un OR para también devolver filas de estudiantes con un GPA de 3.9.
* SELECT * FROM students WHERE last_name < 'M' OR gpa = 3.9;

### Mostró filas donde una de las condiciones era verdadera; había una más que la vez pasada. Ingresa el comando anterior, pero usa AND para ver solo a los estudiantes que cumplen ambas condiciones.
* SELECT * FROM students WHERE last_name < 'M' AND gpa = 3.9;

### Ahora solo muestra filas donde ambas condiciones son verdaderas, una persona. Ingresa el comando anterior, pero añade una tercera condición de OR gpa < 2.3.
* SELECT * FROM students WHERE last_name < 'M' AND gpa = 3.9 OR gpa < 2.3;

### Esto mostró a todos los estudiantes cuyo GPA es menor a 2.3 porque la condición final OR era verdadera para ellos. No importaba con qué letra empezaba su apellido. Puedes agrupar condiciones juntas con paréntesis de esta manera: `WHERE <condition_1> AND (<condition_2> OR <condition_3>)`. Esto solo devolvería filas donde `<condition_1>` sea verdadera y una de las otras también sea verdadera. Visualiza a los estudiantes cuyo apellido es antes de M y que tienen un GPA de 3.9 o menos de 2.3.
* SELECT * FROM students WHERE last_name < 'M' AND (gpa = 3.9 OR gpa < 2.3);

### Dos estudiantes cumplen con esas condiciones. De vuelta en el archivo de información de los estudiantes, agrega un comando echo al final para imprimir las filas sugeridas.
*echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE last_name >= 'R' AND (gpa > 3.8 OR gpa < 2.0)")"

### Ejecuta el script: 
./student_info.sh
```
~~ My Computer Science Students ~~


First name, last name, and GPA of students with a 4.0 GPA:
Casares|Hijo|4.0
Vanya|Hassanah|4.0
Dejon|Howell|4.0

All course names whose first letter is before 'D' in the alphabet:
Computer Networks
Computer Systems
Artificial Intelligence
Calculus
Algorithms

First name, last name, and GPA of students whose last name begins with an 'R' or after and have a GPA greater than 3.8 or less than 2.0:
Efren|Reilly|3.9
Mariana|Russel|1.8
Mehdi|Vandenberghe|1.9
```
### Continuando. Agregue otro comando echo, como los demás, con una oración que diga: Apellido de los estudiantes cuyo apellido contiene una "sa" que no distingue entre mayúsculas y minúsculas o tiene una "r" como segunda letra de la última:

*echo -e "\nLast name of students whose last name contains a case insensitive 'sa' or have an 'r' as the second to last letter:"

### Empiece por ver todo de la tabla courses:
*SELECT * FROM courses;

### Hay algunos que contienen la palabra algoritmos. Puedes usar LIKE para buscar patrones en un texto como este: WHERE <column> LIKE '<pattern>'. Un guión bajo (_) en un patrón devolverá las filas que tengan cualquier carácter en ese lugar. Mira las filas en esta tabla con un nombre de curso que coincida con el patrón '_lgorithms'.
*SELECT * FROM courses WHERE course LIKE '_lgorithms';

### Ese patrón coincidió únicamente con las filas que tenían exactamente un carácter, seguido de algoritmos. Otro carácter del patrón es %. Significa que puede haber cualquier cosa. Para buscar nombres que comiencen con W, puede usar W%. Vea los cursos que terminan e*n algoritmos.
*SELECT * FROM courses WHERE course LIKE '%lgorithms';

### Encontró dos a la vez. Trate viendo cursos que empiesen con web:
*SELECT * FROM courses WHERE course LIKE 'Web%';

### Combine los dos caracteres que coinciden con el patrón para mostrar los cursos que tienen una segunda letra e.
*SELECT * FROM courses WHERE course LIKE '_e%';

### ¡Buen trabajo! Prueba a ver los cursos que tienen un espacio en el nombre.
*SELECT * FROM courses WHERE course LIKE '% %';

### Ahí están. Puedes usar NOT LIKE para buscar elementos que no coincidan con un patrón. Ver cursos que no contengan un espacio.
*SELECT * FROM courses WHERE course NOT LIKE '% %';

### Cinco cursos sin espacio. Intenta encontrar los que contienen una A.
*SELECT * FROM courses WHERE course LIKE '%A%';

### 6 filas. Esto muestra todos los cursos con A mayúscula. ILIKE ignorará el uso de mayúsculas y minúsculas al hacer la correspondencia. Úselo para ver los cursos con A o a.
*SELECT * FROM courses WHERE course ILIKE '%A%';

### Encontró 11 filas en ese momento. También puedes poner NOT delante de ILIKE. Úsalo para ver los cursos que no contienen una A o una a.
*students=> SELECT * FROM courses WHERE course NOT ILIKE '%A%';

### Combina estas condiciones como cualquier otra. Observa los cursos que no tienen A mayúscula o minúscula y tienen un espacio.
*SELECT * FROM courses WHERE course NOT ILIKE '%A%' AND course LIKE '% %';

### En el script de información del estudiante, agregue una declaración echo en la parte inferior como la otra para imprimir los resultados de la consulta sugerida.
*echo "$($PSQL "SELECT last_name FROM students WHERE last_name ILIKE '%sa%' OR last_name LIKE '%r_'")"

### Ejecute el script: 
* ./student_info.sh
```

~~ My Computer Science Students ~~


First name, last name, and GPA of students with a 4.0 GPA:
Casares|Hijo|4.0
Vanya|Hassanah|4.0
Dejon|Howell|4.0

All course names whose first letter is before 'D' in the alphabet:
Computer Networks
Computer Systems
Artificial Intelligence
Calculus
Algorithms

First name, last name, and GPA of students whose last name begins with an 'R' or after and have a GPA greater than 3.8 or less than 2.0:
Efren|Reilly|3.9
Mariana|Russel|1.8
Mehdi|Vandenberghe|1.9

Last name of students whose last name contains a case insensitive 'sa' or have an 'r' as the second to last letter:
Gilbert
Savage
Saunders
Hilpert
Hassanah
```
### Parece que cinco estudiantes cumplen esas condiciones. Agregue otro comando echo en la parte inferior, como los demás. Haga que éste diga: Nombre, apellido y GPA de los estudiantes que no han seleccionado una especialidad y cuyo nombre comienza con "D" o tienen un GPA mayor a 3.0:
*echo -e "\nFirst name, last name, and GPA of students who have not selected a major and either their first name begins with 'D' or they have a GPA greater than 3.0:"

### Mire todos los datos en la tabla students:
* SELECT * FROM students;
 
### Todos los campos que están vacíos o en blanco son nulos. Puedes acceder a ellos usando IS NULL como condición de la siguiente manera: WHERE <column> IS NULL. Ver los estudiantes que no tienen un GPA.
* SELECT * FROM students WHERE gpa IS NULL;
 
### A la inversa, puedes usar IS NOT NULL para ver las filas que no son nulas. Ver toda la información sobre los estudiantes que sí tienen un GPA.
* SELECT * FROM students WHERE gpa IS NOT NULL;

### Ver toda la información de los alumnos que no han elegido carrera.
* SELECT * FROM students WHERE major_id IS NULL;

### Vea los estudiantes que no tienen una especialidad, pero no incluya a los estudiantes sin un GPA.
*SELECT * FROM students WHERE major_id IS NULL AND gpa IS NOT NULL;

### Uno más. Vea los estudiantes que no tienen especialidad ni promedio.
*SELECT * FROM students WHERE major_id IS NULL AND gpa IS NULL;

### En su script, agregue un comando echo en la parte inferior para imprimir los resultados que busca la consulta.
*echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE major_id IS NULL AND (first_name LIKE 'D%' OR gpa > 3.0)")"

### Ejecute el script para ver si los estudiantes que reunen esas condiciones:

### Son tres. Añade otra frase, como las otras, que diga Nombre del curso de los cinco primeros cursos, en orden alfabético inverso, que tengan una "e" como segunda letra o terminen con una "s":
*echo -e "\nCourse name of the first five courses, in reverse alphabetical order, that have an 'e' as the second letter or end with an 's':"

### Puede especificar el orden en el que desea que aparezcan los resultados agregando ORDER BY <column_name> al final de una consulta. En el indicador psql, visualice toda la información en la tabla de estudiantes ordenada por GPA.
*SELECT * FROM students ORDER BY gpa;

### Esto coloca los promedios más bajos en la parte superior. Al usar ORDER BY, se ordenará en orden ascendente (ASC) de manera predeterminada. Agregue DESC (descendente) al final de la última consulta para colocar los más altos en la parte superior.
*SELECT * FROM students ORDER BY gpa DESC;

### Ahora, los promedios más altos se encuentran en la parte superior. Puedes agregar más columnas al orden separándolas con una coma de la siguiente manera: ORDER BY <column_1>, <column_2>. Los valores que coincidan en la primera columna ordenada se ordenarán por la siguiente. Mira toda la información de los estudiantes con los promedios más altos en la parte superior y en orden alfabético por nombre si los promedios coinciden.
*SELECT * FROM students ORDER BY gpa DESC, first_name;

### Muchas veces, solo desea devolver una cierta cantidad de filas. Puede agregar LIMIT <number> al final de la consulta para obtener solo la cantidad que desea. Vea los estudiantes en el mismo orden que el último comando, pero solo devuelva las primeras 10 filas.
*SELECT * FROM students ORDER BY gpa DESC, first_name LIMIT 10;

### El orden de las palabras clave en la consulta es importante. No se puede poner LIMIT antes de ORDER BY, ni ninguna de ellas antes de WHERE. Visualiza la misma cantidad de estudiantes, en el mismo orden, pero no incluyas a los que no tienen un promedio de calificaciones.
*SELECT * FROM students WHERE gpa IS NOT NULL ORDER BY gpa DESC, first_name LIMIT 10;

### En su script, agregue el comando echo para imprimir las filas que solicita la sentencia.

*echo "$($PSQL "SELECT course FROM courses WHERE course LIKE '_e%' OR course LIKE '%s' ORDER BY course DESC LIMIT 5")"

### Ejecute el script para ver los cursos:./student_info.sh

### 😎 Agrega otro comando echo al final del script como los demás. Haz que este diga: Promedio de calificaciones de todos los estudiantes redondeado a dos decimales:
* echo -e "\nAverage GPA of all students rounded to two decimal places:"

### Hay varias funciones matemáticas que se pueden usar con columnas numéricas. Una de ellas es MIN, que se puede usar al seleccionar una columna de la siguiente manera: SELECT MIN(<column>) FROM <table>. Encontrará el valor más bajo en la columna. En el indicador de psql, vea el valor más bajo en la columna gpa de la tabla students.
* SELECT MIN(gpa) FROM students;

### Otro es MAX, úsalo para ver el promedio más grande de la misma tabla.
* SELECT MAX(gpa) FROM students;

### De la misma manera, utilice la función SUMA para averiguar cuánto suman todos los valores de la columna major_id en la tabla students.
* SELECT SUM(major_id) FROM students;

### AVG le proporcionará el promedio de todos los valores de una columna. Úselo para ver el promedio de la misma columna.
* SELECT AVG(major_id) FROM students;
 
### Puede redondear decimales hacia arriba o hacia abajo hasta el número entero más cercano con CEIL y FLOOR, respectivamente. Utilice CEIL para redondear el promedio de major_id hasta el número entero más cercano. A continuación, se muestra un ejemplo: CEIL(<number_to_round>).
* SELECT CEIL(AVG(major_id)) FROM students;

### O bien, puede redondear un número al número entero más cercano con ROUND. Úselo para redondear el promedio de la columna major_id al número entero más cercano
* SELECT ROUND(AVG(major_id)) FROM students;

### Puede redondear a una cantidad específica de decimales agregando una coma y un número a ROUND, de la siguiente manera: ROUND(<number_to_round>, <decimals_places>). Redondee el promedio de major_id a cinco decimales.
* SELECT ROUND(AVG(major_id), 5) FROM students;

### Ahora deberías poder encontrar lo que solicita tu script. Agrega el comando para imprimirlo.
*echo "$($PSQL "SELECT ROUND(AVG(gpa), 2) FROM students")"

### Ejecute el script : ./student_info.sh
```
~~ My Computer Science Students ~~


First name, last name, and GPA of students with a 4.0 GPA:
Casares|Hijo|4.0
Vanya|Hassanah|4.0
Dejon|Howell|4.0

All course names whose first letter is before 'D' in the alphabet:
Computer Networks
Computer Systems
Artificial Intelligence
Calculus
Algorithms

First name, last name, and GPA of students whose last name begins with an 'R' or after and have a GPA greater than 3.8 or less than 2.0:
Efren|Reilly|3.9
Mariana|Russel|1.8
Mehdi|Vandenberghe|1.9

Last name of students whose last name contains a case insensitive 'sa' or have an 'r' as the second to last letter:
Gilbert
Savage
Saunders
Hilpert
Hassanah

First name, last name, and GPA of students who have not selected a major and either their first name begins with 'D' or they have a GPA greater than 3.0:
Noe|Savage|3.6
Danh|Nhung|2.4
Hugo|Duran|3.8

Course name of the first five courses, in reverse alphabetical order, that have an 'e' as the second letter or end with an 's':
Web Programming
Web Applications
Server Administration
Network Security
Database Systems

Average GPA of all students rounded to two decimal places:
3.09
```
### Lo estas haciendo bastante bien. Agregue otro comando para imprimir el ID de la carrera, el número total de estudiantes en una columna llamada 'number_of_students' y el promedio de calificaciones redondeado a dos decimales en una columna llamada 'average_gpa', para cada ID de carrera en la tabla de estudiantes que tenga un recuento de estudiantes mayor que 1:
* echo -e "\nMajor ID, total number of students in a column named 'number_of_students', and average GPA rounded to two decimal places in a column name 'average_gpa', for each major ID in the students table having a student count greater than 1:"

### Otra función es COUNT. Puedes usarla de esta manera: COUNT(<column>). Te dirá cuántas entradas hay en una tabla para la columna. Pruébala en el indicador psql usando COUNT(*) para ver cuántas especialidades hay.
*SELECT COUNT(*) FROM majors;

### Usando el mismo método, verifica cuántos estudiantes tienes.
* SELECT COUNT(*) FROM students;

### Al usar * de esa manera, se indica cuántas filas en total hay en la tabla. Vea el recuento de la columna major_id en la tabla students para ver cuántos de sus estudiantes han elegido una especialidad.
*SELECT COUNT(major_id) FROM students;

### El uso de major_id no contabilizó los valores nulos en esa columna. 23 estudiantes tienen una especialidad. DISTINCT es una función que le mostrará solo valores únicos. Puede usarla de esta manera: DISTINCT(<column>). Vea los valores únicos de major_id en la tabla students.
*SELECT DISTINCT(major_id) FROM students;

### Hay seis valores de major_id únicos en la tabla students. Puedes obtener los mismos resultados con GROUP BY. Aquí tienes un ejemplo de cómo usarlo: SELECT <column> FROM <table> GROUP BY <column>. Usa este método para ver los valores de major_id únicos en la tabla students nuevamente.
*SELECT major_id FROM students GROUP BY major_id;

### El resultado fue el mismo que DISTINCT, pero con GROUP BY puedes agregar cualquiera de las funciones agregadas (MIN, MAX, COUNT, etc.) para encontrar más información. Por ejemplo, si quisieras ver cuántos estudiantes había en cada carrera, podrías usar SELECT COUNT(*) FROM students GROUP BY major_id. Visualiza la columna major_id y la cantidad de estudiantes en cada major_id.
*SELECT major_id, COUNT(*) FROM students GROUP BY major_id;

### Al utilizar GROUP BY, todas las columnas del área SELECT deben incluirse en el área GROUP BY. Las demás columnas deben utilizarse con cualquiera de las funciones de agregación (MAX, AVG, COUNT, etc.).
Vuelva a ver los valores únicos de major_id con GROUP BY, pero vea cuál es el promedio de calificaciones más bajo en cada uno de ellos.
*SELECT major_id, MIN(gpa) FROM students GROUP BY major_id;

### Buen trabajo. Introduce la misma consulta, pero añade una columna que muestre también el promedio de calificaciones más alto en cada especialidad.
*SELECT major_id, MIN(gpa), MAX(gpa) FROM students GROUP BY major_id;

### Otra opción con GROUP BY es HAVING. Puedes agregarla al final de esta manera: SELECT <column> FROM <table> GROUP BY <column> HAVING <condition>. 
La condición debe ser una función de agregación con una prueba. Un ejemplo podría ser usar HAVING COUNT(*) > 0 para mostrar solo las columnas agrupadas que tengan al menos una fila. 
Usa HAVING para mostrar solo las filas de la última consulta que tengan un GPA máximo de 4.0.
*SELECT major_id, MIN(gpa), MAX(gpa) FROM students GROUP BY major_id HAVING MAX(gpa) = 4.0;

### Dos de tus carreras tienen al menos un estudiante con un GPA de 4.0. Al observar los resultados, la columna se llama min. Puedes cambiar el nombre de una columna con AS de esta manera: SELECT <column> AS <new_column_name> Ingresa el mismo comando, pero cambia el nombre de la columna min a min_gpa.
*SELECT major_id, MIN(gpa) AS min_gpa, MAX(gpa) FROM students GROUP BY major_id HAVING MAX(gpa) = 4.0;

### Ahora la columna tiene un nombre mejor. Ingrese el mismo comando, pero cambie el nombre de la columna máxima a max_gpa también.
*SELECT major_id, MIN(gpa) AS min_gpa, MAX(gpa) AS max_gpa FROM students GROUP BY major_id HAVING MAX(gpa) = 4.0;

### Esto es más descriptivo. Vea el major_id y la cantidad de estudiantes en cada major_id en una columna llamada number_of_students.
*SELECT major_id, COUNT(*) AS number_of_students FROM students GROUP BY major_id;

### Utilice HAVING con la última consulta para mostrar solo las filas con menos de ocho estudiantes en la especialidad.
*SELECT major_id, COUNT(*) AS number_of_students FROM students GROUP BY major_id HAVING COUNT(*) < 8;

### Bien hecho. En el script, agrega el comando para imprimir los resultados sugeridos.
*echo "$($PSQL "SELECT major_id, COUNT(*) AS number_of_students, ROUND(AVG(gpa),2) AS average_gpa FROM students GROUP BY major_id HAVING COUNT(*) > 1")"

### Ejecute el script para ver el resultado.
 ./student_info.sh
``` 
 
~~ My Computer Science Students ~~


First name, last name, and GPA of students with a 4.0 GPA:
Casares|Hijo|4.0
Vanya|Hassanah|4.0
Dejon|Howell|4.0

All course names whose first letter is before 'D' in the alphabet:
Computer Networks
Computer Systems
Artificial Intelligence
Calculus
Algorithms

First name, last name, and GPA of students whose last name begins with an 'R' or after and have a GPA greater than 3.8 or less than 2.0:
Efren|Reilly|3.9
Mariana|Russel|1.8
Mehdi|Vandenberghe|1.9

Last name of students whose last name contains a case insensitive 'sa' or have an 'r' as the second to last letter:
Gilbert
Savage
Saunders
Hilpert
Hassanah

First name, last name, and GPA of students who have not selected a major and either their first name begins with 'D' or they have a GPA greater than 3.0:
Noe|Savage|3.6
Danh|Nhung|2.4
Hugo|Duran|3.8

Course name of the first five courses, in reverse alphabetical order, that have an 'e' as the second letter or end with an 's':
Web Programming
Web Applications
Server Administration
Network Security
Database Systems

Average GPA of all students rounded to two decimal places:
3.09

Major ID, total number of students in a column named 'number_of_students', and average GPA rounded to two decimal places in a column name 'average_gpa', for each major ID in the students table having a student count greater than 1:
|8|2.97
41|6|3.53
38|4|2.73
36|6|2.92
37|6|3.38
```
### Agregue un comando echo a su script como los demás que imprime una lista de carreras, en orden alfabético, que ningún estudiante está tomando o tiene un estudiante cuyo nombre contiene una 'ma' que no distingue entre mayúsculas y minúsculas:
*echo -e "\nList of majors, in alphabetical order, that either no student is taking or has a student whose first name contains a case insensitive 'ma':"

### Las tablas de especialidades y estudiantes están vinculadas con la clave externa major_id. Si desea ver el nombre de la especialidad que cursa un estudiante, debe UNIR las dos tablas en una sola. A continuación, se muestra un ejemplo de cómo hacerlo:
SELECT * FROM <table_1> FULL JOIN <table_2> ON <table_1>.<foreign_key_column> = <table_2>.<foreign_key_column>;

### En el indicador de psql, una las dos tablas con el método anterior.

*SELECT * FROM students FULL JOIN majors ON students.major_id = majors.major_id;

### Se muestran todas las columnas de ambas tablas, las dos columnas major_id son las mismas en cada fila para las que la tienen. Puedes ver que hay algunos estudiantes sin una especialidad y algunas especialidades sin estudiantes. La UNIÓN COMPLETA que usaste incluirá todas las filas de ambas tablas, tengan o no una fila que use esa clave externa en la otra. A partir de ahí, puedes usar cualquiera de los métodos anteriores para acotar, agrupar, ordenar, etc. Usa una UNIÓN IZQUIERDA para unir las mismas dos tablas de la misma manera.
*SELECT * FROM students LEFT JOIN majors ON students.major_id = majors.major_id;

### Hay unas pocas filas menos que en la última consulta. En el LEFT JOIN que usaste, la tabla students fue la tabla de la izquierda ya que estaba en el lado izquierdo del JOIN. majors fue la tabla de la derecha. Un LEFT JOIN obtiene todas las filas de la tabla de la izquierda, pero solo las filas de la tabla de la derecha que están vinculadas desde la tabla de la izquierda. Al mirar los datos, puedes ver que se devolvieron todos los estudiantes, pero las especialidades sin ningún estudiante no fueron incluidas. Ahora une las mismas dos tablas con un RIGHT JOIN esta vez
*SELECT * FROM students RIGHT JOIN majors ON students.major_id = majors.major_id;

### La unión derecha(RIGTH JOIN) mostró todas las filas de la tabla derecha (majors), pero sólo las filas de la tabla izquierda (students) si tienen una especialización. Hay un tipo más que debes conocer. Une las dos tablas con INNER JOIN.
* SELECT * FROM students INNER JOIN majors ON students.major_id = majors.major_id;

### La combinación INNER JOIN solo devolvió los estudiantes que tienen una especialización y las especializaciones que tienen un estudiante. En otras palabras, solo devolvió filas si tienen un valor en la columna de clave externa (major_id) de la tabla opuesta. Ahora debería saber un poco sobre los cuatro tipos principales de combinaciones. Intente usar una combinación LEFT JOIN para mostrar todas las especializaciones pero solo los estudiantes que tienen una especialización.
*SELECT * FROM majors LEFT JOIN students ON majors.major_id = students.major_id;

### Excelente. Todas las carreras están ahí. A continuación, utilice la combinación adecuada para mostrar solo los estudiantes que están inscritos en una carrera y solo las carreras que tienen un estudiante inscrito en ellas.
*SELECT * FROM majors INNER JOIN students ON majors.major_id = students.major_id;

### 👍 Intenta usar una unión correcta para mostrar todos los estudiantes pero solo las especialidades si un estudiante está inscrito en ellas.
*SELECT * FROM majors RIGHT JOIN students ON majors.major_id = students.major_id;

### Esto mostró a todos los estudiantes, ya que era la tabla correcta de la UNIÓN DERECHA. Use la unión adecuada con las mismas dos tablas para mostrar todas las filas en ambas tablas, ya sea que tengan un valor en la columna de clave externa o no.
*SELECT * FROM majors FULL JOIN students ON majors.major_id = students.major_id;

### Hagamos algunos experimentos más con uniones. Digamos que quieres encontrar una lista de carreras que están cursando los estudiantes. Utiliza la JOIN más eficiente para unir las dos tablas que necesitas. Por ahora, solo une las tablas, no utilices ninguna otra condición.
*SELECT * FROM students INNER JOIN majors ON students.major_id = majors.major_id;

### Bien. Para obtener la lista, no necesitas todas las columnas. Introduce el mismo comando, pero obtén solo la columna que necesitas.
*SELECT major FROM students INNER JOIN majors ON students.major_id = majors.major_id;

### Tampoco conviene que haya duplicados. Utilice DISTINCT para obtener solo los únicos y ver la lista de carreras que tienen estudiantes.
*SELECT DISTINCT(major) FROM students INNER JOIN majors ON students.major_id = majors.major_id;

### Aquí tienes la lista de carreras que están cursando los estudiantes 😄 Ahora, digamos que quieres una lista de carreras que no están cursando los estudiantes. Usa la opción JOIN más eficiente para unir las dos tablas que necesitas. Solo une las tablas por ahora, no uses ninguna otra condición.
*SELECT * FROM students RIGHT JOIN majors ON students.major_id = majors.major_id;

### Eso te dio todas las especialidades, puedes ver las que no tienen estudiantes. Agrega una condición WHERE para ver solo las especialidades sin estudiantes, usa student_id en su condición.
SELECT * FROM students RIGHT JOIN majors ON students.major_id = majors.major_id WHERE student_id IS NULL;

### Ahora solo tienes las filas que necesitas. Obtén solo las columnas que necesitas para ver la lista de especialidades sin estudiantes.
*SELECT major FROM students RIGHT JOIN majors ON students.major_id = majors.major_id WHERE student_id IS NULL;

### Lo estás haciendo genial. A continuación, usa el 'JOIN' más eficiente para unir las tablas que necesitarías si te pidieran obtener el nombre, apellido, especialidad y GPA de los estudiantes que están tomando Data Science o tienen un GPA de 3.8 o superior. Solo une las tablas por ahora, no uses ninguna otra condición.
*SELECT * FROM students LEFT JOIN majors ON students.major_id = majors.major_id;

### Ingresa el mismo comando, pero usa WHERE para obtener solo los estudiantes que cumplen con los requisitos. Como recordatorio, el objetivo era encontrar estudiantes que estén tomando Data Science o tengan un GPA de 3.8 o superior.
*SELECT * FROM students LEFT JOIN majors ON students.major_id = majors.major_id WHERE major='Data Science' OR gpa >= 3.8;

### Ahora, has reducido las filas que estás buscando. Ingresa el mismo comando, pero solo obtén las columnas que necesitas. Eran cuatro: el nombre, apellido, especialidad y GPA de los estudiantes. Obténlas en ese orden.
*SELECT first_name, last_name, major, gpa FROM students LEFT JOIN majors ON students.major_id = majors.major_id WHERE major='Data Science' OR gpa >= 3.8;

### Desde allí, podrías ponerlos en un orden específico si lo deseas o limitar los resultados a una cierta cantidad, entre otras cosas. Por último, usa el 'JOIN' más eficiente para unir las tablas que necesitarías si te pidieran obtener el nombre y la especialidad de los estudiantes cuyo first_name o la especialidad contenga "ri". Solo une las tablas por ahora, no uses ninguna otra condición.
*SELECT * FROM students FULL JOIN majors ON students.major_id = majors.major_id;

### Agrega un WHERE a la consulta anterior para que solo obtengas las filas que necesitas. Las filas que querías eran las que tienen un nombre o una especialidad que contenga "ri".
*SELECT * FROM students FULL JOIN majors ON students.major_id = majors.major_id WHERE first_name LIKE '%ri%' OR major LIKE '%ri%';

### Finalmente, solo querías mostrar las columnas first_name y major. Ingresa la consulta anterior, pero solo obtén las columnas que necesitas.
*SELECT first_name, major FROM students FULL JOIN majors ON students.major_id = majors.major_id WHERE first_name LIKE '%ri%' OR major LIKE '%ri%';

### En su script, agregue el comando para imprimir lo que la sentencia solicita.
*echo "$($PSQL "SELECT major FROM students FULL JOIN majors ON students.major_id = majors.major_id WHERE major IS NOT NULL AND (student_id IS NULL OR first_name ILIKE '%ma%') ORDER BY major")"

### Ejecute el script : ./student_info.sh
```
~~ My Computer Science Students ~~


First name, last name, and GPA of students with a 4.0 GPA:
Casares|Hijo|4.0
Vanya|Hassanah|4.0
Dejon|Howell|4.0

All course names whose first letter is before 'D' in the alphabet:
Computer Networks
Computer Systems
Artificial Intelligence
Calculus
Algorithms

First name, last name, and GPA of students whose last name begins with an 'R' or after and have a GPA greater than 3.8 or less than 2.0:
Efren|Reilly|3.9
Mariana|Russel|1.8
Mehdi|Vandenberghe|1.9

Last name of students whose last name contains a case insensitive 'sa' or have an 'r' as the second to last letter:
Gilbert
Savage
Saunders
Hilpert
Hassanah
Noe|Savage|3.6
Danh|Nhung|2.4
Hugo|Duran|3.8

Course name of the first five courses, in reverse alphabetical order, that have an 'e' as the second letter or end with an 's':
Web Programming
Web Applications
Server Administration
Network Security
Database Systems

Average GPA of all students rounded to two decimal places:
3.09

Major ID, total number of students in a column named 'number_of_students', and average GPA rounded to two decimal places in a column name 'average_gpa', for each major ID in the students table having a student count greater than 1:
|8|2.97
41|6|3.53
38|4|2.73
36|6|2.92
37|6|3.38

List of majors, in alphabetical order, that either no student is taking or has a student whose first name contains a case insensitive 'ma':
Computer Programming
Database Administration
Network Engineering
Web Development
```

### 😄 Ya casi está. En tu script, agrega un comando para imprimir esta oración como las demás: Lista de cursos únicos, en orden alfabético inverso, que ningún estudiante u "Obie Hilpert" está tomando:
*echo -e "\nList of unique courses, in reverse alphabetical order, that no student or 'Obie Hilpert' is taking:"

### Repasemos algunas cosas más antes de averiguar cómo ver los cursos que está tomando un estudiante. Comience por realizar un FULL JOIN en las tablas de students y majors.
*SELECT * FROM students FULL JOIN majors ON students.major_id = majors.major_id;

### Si observa los nombres de las columnas, se muestran dos columnas major_id. Una de la tabla students y otra de la tabla majors. Si intentara consultarla usando major_id, obtendría un error. Necesitaría especificar de qué tabla desea la columna de esta manera: <table>.<column>. Ingrese la misma combinación pero solo obtenga la columna major_id de la tabla students.
*SELECT students.major_id FROM students FULL JOIN majors ON students.major_id = majors.major_id;

### Anteriormente, se utilizaba AS para cambiar el nombre de las columnas. También se puede utilizar para cambiar el nombre de las tablas o darles alias. A continuación, se incluye un ejemplo: SELECT * FROM <table> AS <new_name>;. Introduzca la misma consulta que acaba de introducir, pero cambie el nombre de la tabla de valores principales a m. En cualquier lugar en el que se haga referencia a la tabla de valores principales, deberá utilizar m en lugar de majors.
*SELECT students.major_id FROM students FULL JOIN majors AS m ON students.major_id = m.major_id;

### Esto no afecta el resultado. Simplemente puede facilitar la lectura de algunas consultas. Ingrese la misma consulta, pero cambie el nombre de la tabla de estudiantes a s también.
*SELECT s.major_id FROM students AS s FULL JOIN majors AS m ON s.major_id = m.major_id;

### Existe una palabra clave de acceso directo, USING, para unir tablas si la columna de clave externa tiene el mismo nombre en ambas tablas. A continuación, se incluye un ejemplo: SELECT * FROM <table_1> FULL JOIN <table_2> USING(<column>);. Utilice este método para ver todas las columnas de la tabla de estudiantes y carreras. No utilice ningún alias.
*SELECT * FROM students FULL JOIN majors USING(major_id);

### Tenga en cuenta que las dos columnas major_id se convirtieron en una con USING. Para saber qué cursos está tomando un estudiante, deberá unir todas las tablas. Puede agregar una tercera tabla a una unión de esta manera: SELECT * FROM <table_1> FULL JOIN <table_2> USING(<column>) FULL JOIN <table_3> USING(<column>). Este ejemplo unirá las dos primeras tablas en una, convirtiéndola en la tabla de la izquierda para la segunda unión. Utilice este método para unir las dos tablas de la consulta anterior con la tabla majors_courses.
*SELECT * FROM students FULL JOIN majors USING(major_id) FULL JOIN majors_courses USING(major_id);

### Es posible que deba ajustar el tamaño de la terminal para alinear la salida. Lo que está viendo es cada combinación única de filas en la base de datos. Los estudiantes con una especialidad se enumeran varias veces, una para cada curso incluido en la especialidad. Las especialidades sin estudiantes están allí junto con los cursos para ellos. Los estudiantes sin una especialidad están incluidos, no tienen cursos y solo se enumeran una vez. Puede unir tantas tablas como desee. Una la última tabla al comando anterior para obtener los nombres de los cursos con toda esta información.
*SELECT * FROM students FULL JOIN majors USING(major_id) FULL JOIN majors_courses USING(major_id) FULL JOIN courses USING(course_id);

### La misma cantidad de filas, pero ahora obtienes los nombres de los cursos. En tu secuencia de comandos, agrega el comando para imprimir la información sugerida.

*echo "$($PSQL "SELECT DISTINCT(course) FROM students RIGHT JOIN majors USING(major_id) INNER JOIN majors_courses USING(major_id) INNER JOIN courses USING(course_id) WHERE (first_name = 'Obie' AND last_name = 'Hilpert') OR student_id IS NULL ORDER BY course DESC")"

### Ejecute el script:
```
~~ My Computer Science Students ~~


First name, last name, and GPA of students with a 4.0 GPA:
Casares|Hijo|4.0
Vanya|Hassanah|4.0
Dejon|Howell|4.0

All course names whose first letter is before 'D' in the alphabet:
Computer Networks
Computer Systems
Artificial Intelligence
Calculus
Algorithms

First name, last name, and GPA of students whose last name begins with an 'R' or after and have a GPA greater than 3.8 or less than 2.0:
Efren|Reilly|3.9
Mariana|Russel|1.8
Mehdi|Vandenberghe|1.9

Last name of students whose last name contains a case insensitive 'sa' or have an 'r' as the second to last letter:
Gilbert
Savage
Saunders
Hilpert
Hassanah
Noe|Savage|3.6
Danh|Nhung|2.4
Hugo|Duran|3.8

Course name of the first five courses, in reverse alphabetical order, that have an 'e' as the second letter or end with an 's':
Web Programming
Web Applications
Server Administration
Network Security
Database Systems

Average GPA of all students rounded to two decimal places:
3.09

Major ID, total number of students in a column named 'number_of_students', and average GPA rounded to two decimal places in a column name 'average_gpa', for each major ID in the students table having a student count greater than 1:
|8|2.97
41|6|3.53
38|4|2.73
36|6|2.92
37|6|3.38

List of majors, in alphabetical order, that either no student is taking or has a student whose first name contains a case insensitive 'ma':
Computer Programming
Database Administration
Network Engineering
Web Development

List of unique courses, in reverse alphabetical order, that no student or 'Obie Hilpert' is taking:
Web Programming
Web Applications
Python
Object-Oriented Programming
Network Security
Data Structures and Algorithms
Computer Systems
Computer Networks
Algorithms
```
### Último. Agregue un comando que imprima la lista de cursos, en orden alfabético, con un solo estudiante inscrito:
*echo -e "\nList of courses, in alphabetical order, with only one student enrolled:"

### Try entering this in the psql prompt: SELECT COUNT(course), COURSE FROM students INNER JOIN majors USING(major_id) INNER JOIN majors_courses USING(major_id) INNER JOIN courses USING(course_id) GROUP BY course;
*echo "$($PSQL "SELECT course FROM students INNER JOIN majors_courses USING(major_id) INNER JOIN courses USING(course_id) GROUP BY course HAVING COUNT(student_id) = 1 ORDER BY course")"

### run the script:
./student_info.sh
```
~~ My Computer Science Students ~~


First name, last name, and GPA of students with a 4.0 GPA:
Casares|Hijo|4.0
Vanya|Hassanah|4.0
Dejon|Howell|4.0

All course names whose first letter is before 'D' in the alphabet:
Computer Networks
Computer Systems
Artificial Intelligence
Calculus
Algorithms

First name, last name, and GPA of students whose last name begins with an 'R' or after and have a GPA greater than 3.8 or less than 2.0:
Efren|Reilly|3.9
Mariana|Russel|1.8
Mehdi|Vandenberghe|1.9

Last name of students whose last name contains a case insensitive 'sa' or have an 'r' as the second to last letter:
Gilbert
Savage
Saunders
Hilpert
Hassanah
Noe|Savage|3.6
Danh|Nhung|2.4
Hugo|Duran|3.8

Course name of the first five courses, in reverse alphabetical order, that have an 'e' as the second letter or end with an 's':
Web Programming
Web Applications
Server Administration
Network Security
Database Systems

Average GPA of all students rounded to two decimal places:
3.09

Major ID, total number of students in a column named 'number_of_students', and average GPA rounded to two decimal places in a column name 'average_gpa', for each major ID in the students table having a student count greater than 1:
|8|2.97
41|6|3.53
38|4|2.73
36|6|2.92
37|6|3.38

List of majors, in alphabetical order, that either no student is taking or has a student whose first name contains a case insensitive 'ma':
Computer Programming
Database Administration
Network Engineering
Web Development

List of unique courses, in reverse alphabetical order, that no student or 'Obie Hilpert' is taking:
Web Programming
Web Applications
Python
Object-Oriented Programming
Network Security
Data Structures and Algorithms
Computer Systems
Computer Networks
Algorithms

List of courses, in alphabetical order, with only one student enrolled:
Computer Networks
Computer Systems
Server Administration
UNIX
```
