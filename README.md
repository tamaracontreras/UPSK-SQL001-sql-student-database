# UPSK-SQL001-sql-student-database

Primero accedemos con **echo sql hello**

Luego nos conectamos a la base de datos con **psql --username=freecodecamp --dbname=postgres**

luego listamos las bases de datos con el comando **\l**

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled.png)

Creamos la base de datos **students**  con el comando **CREATE DATABASE students**

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%201.png)

Verificamos que nuestra base de datos haya sido creada con el comando : **/l**

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%202.png)

Nos conectamos a la base de datos creada con el comando **\c  + nombre de la basede datos** 

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%203.png)

Nos indican que : Los archivos CSV tienen un grupo de estudiantes con información sobre ellos y algunos cursos y especialidades. Tendrás cuatro tablas. Uno para los estudiantes y su información, uno para cada especialidad, otro para cada curso y uno final para mostrar qué cursos están incluidos en cada especialidad. Primero, cree la tabla de estudiantes.

La creamos con el comando **CREATE TABLE nombre_de_la_tabla();**

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%204.png)

La segunda tabla será para cada especialización única que aparece en los datos.Crea una tabla llamada majors.

La creamos de la misma manera que anteriormente

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%205.png)

La tercera tabla se llamará **courses**

La creamos de la misma manera

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%206.png)

La tabla final será una tabla de unión para las especialidades y cursos. Créelo con el nombre **majors_courses.**

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%207.png)

Utilice el comando de acceso directo de visualización para ver sus tablas y asegurarse de que está satisfecho con ellas.

para ello debemos usar el comando **\d**

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%208.png)

Sobre las columnas. El archivo Students.csv tiene cuatro campos; creará una columna para cada uno de ellos, así como una columna de ID. Agregue una columna a la tabla de estudiantes llamada **Student_id**. Dale un tipo de SERIAL para que incremente automáticamente y conviértelo en CLAVE PRIMARIA.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%209.png)

La primera columna en Students.csv es **first_name.** Agregue una columna a la tabla de estudiantes con ese nombre. Conviértalo en un tipo de VARCHAR(50) y asígnele la restricción NOT NULL.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2010.png)

La siguiente columna de datos es last_name. Agréguela a la tabla students. Asígnele el mismo tipo de datos y la misma longitud máxima que first_name y asegúrese de que tenga la restricción NOT NULL.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2011.png)

La siguiente columna es para especialidad(major). Dado que tendrá cada especialidad en otra tabla, esta columna será una clave externa que la referencia. Cree una columna en la tabla de estudiantes llamada major_id y asígnele un tipo de datos INT por ahora. Volverá y establecerá la clave externa más tarde.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2012.png)

Crea la última columna, gpa. Los datos del CSV muestran que son decimales con una longitud de 2 y que hay un número a la derecha del decimal. Asígnale un tipo de datos de NUMERIC(2,1).

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2013.png)

Utilice el comando de acceso directo para mostrar los detalles de la tabla de estudiantes para asegurarse de que le guste.

para eso usamos **\d nombredelatabla**

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2014.png)

Aún falta la clave externa (forent key). A continuación, completemos la tabla de claves principales. Agreguemos una columna major_id. Conviértala en un tipo SERIAL y la CLAVE PRINCIPAL para esta tabla.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2015.png)

Esta tabla solo tendrá otra columna para el nombre de la especialidad(MAJOR). Agregue una columna llamada especialidad(MAJOR). Conviértala en un VARCHAR con una longitud máxima de 50 y asígnele la restricción NOT NULL.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2016.png)

Consulta los detalles de la tabla de las principales carreras para asegurarte de que te gusta.

para eso usamos el comando **\d nombre_de_tabla**

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2017.png)

Esta tabla se ve bien. Ahora, configure la columna major_id de la tabla students como una clave externa que haga referencia a la columna major_id de la tabla majors. Aquí hay un ejemplo de cómo hacerlo: ALTER TABLE <table_name> ADD FOREIGN KEY(<column_name>) REFERENCES <referenced_table_name>(<referenced_column_name>);

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2018.png)

Vea los detalles de la tabla students otra vez para asegurarte de que la key esta ahí

para eso usamos el comando **\d nombre de la tabla**

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2019.png)

A continuación, está la tabla de courses. Añádele una columna course_id. Asígnale un tipo SERIAL y conviértela en la clave principal.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2020.png)

Agregue una columna course a la tabla de courses que sea de tipo VARCHAR. Los nombres de los cursos son un poco más largos, por lo que debe darles una longitud máxima de 100. Además, asegúrese de que no pueda aceptar valores nulos.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2021.png)

> Para borrar una columna con datos erroneos
> 

> **ALTER TABLE nombre_tabla DROP COLUMN column_b**;
> 

Vea los detalles de la tabla de cursos para asegurarse de que se vea bien.

Lo hacemos con el comando **\d courses**

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2022.png)

Falta una tabla más. La tabla de unión majors_courses tendrá dos columnas, cada una de las cuales hace referencia a la clave principal de dos tablas relacionadas. Primero, agrégale una columna major_id. Por ahora, solo dale un tipo INT.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2023.png)

Establezca la columna major_id que acaba de crear como una clave externa (FOREIGN KEY) que haga referencia a la columna major_id de la tabla majors.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2024.png)

Agregue la columna  course_id a la tabla majors_courses de tipo INT

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2025.png)

Establezca su nueva columna course_id como una clave externa(FOREIGN KEY) que haga referencia a la otra columna course_id.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2026.png)

Utilice el comando de acceso directo para mostrar los detalles de la tabla de estudiantes para asegurarse de que le guste.

para eso usamos \d nombredelatabla

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2027.png)

Falta algo. Esta tabla no tiene una clave principal. Los datos de courses.csv irán en esta tabla. Una única especialidad aparecerá en ella varias veces, y lo mismo con un curso. Por lo tanto, ninguno de ellos puede ser una clave principal. Pero nunca habrá una fila con los mismos dos valores que otra fila. Por lo tanto, las dos columnas juntas son únicas. Puede crear una clave principal compuesta que use más de una columna como un par único de esta manera: ALTER TABLE <table_name> ADD PRIMARY KEY(<column_name>, <column_name>); Agregue una clave principal compuesta a la tabla usando las dos columnas.

Esto hace que no se pueda repetir los cursos y las especialidad , es decir no habrán filas duplicadas

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2028.png)

Verificar los detalles con **\d majors_courses**

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2029.png)

Terminamos , ahora veamos las tablas que terminaste.

Con el comando : \d

El comando \d en SQL se utiliza para mostrar la estructura de las tablas, vistas, secuencias y otros objetos en la base de datos. Proporciona detalles sobre las columnas, su tipo de datos, restricciones y claves asociadas.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2030.png)

A continuación, puedes comenzar a agregar información. Dado que la tabla de estudiantes necesita un major_id, puedes agregar primero una especialidad. Consulta los detalles de la tabla de especialidades para ver qué información espera.

La consulta se hace con el comando **\d majors**

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2031.png)

Solo necesita el nombre de una especialidad. El ID se agregará automáticamente. Agregue la primera especialidad del archivo courses.csv a la tabla de especialidades. Es un VARCHAR, así que asegúrese de poner el valor entre comillas simples.

con este comando agregamos info a la columna major de la tabla majors el valor Database Administration

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2032.png)

Utilice SELECT para ver todos los datos en la tabla de especialidades para asegurarse de que se insertaron correctamente.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2033.png)

Inserta el primer curso desde courses.csv en la tabla courses

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2034.png)

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2035.png)

Mira todos los datos en la tabla courses , para asegurarse de que se hayan agregado

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2036.png)

A continuación, puede agregar una fila a la tabla de uniones. Vea los detalles de la misma para ver qué espera.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2037.png)

Quiere un major_id y un course_id. Agregue una fila a majors_courses para la primera entrada en courses.csv.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2038.png)

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2039.png)

Vea todos los datos de la tabla que acaba de agregar.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2040.png)

Parece que se agregó la fila. Vea los detalles de la tabla de estudiantes para recordar qué espera y poder agregar el primer estudiante a la base de datos.

Con el comando : **\d students**

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2041.png)

El resultado muestra lo que necesita la tabla. Inserte la primera persona de students.csv en la tabla students.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2042.png)

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2043.png)

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2044.png)

A continuación solucione el error que cometí, ya que ingrese el registro dos veces 

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2045.png)

Bien, has añadido una fila a cada tabla. Puede que sea conveniente revisar los datos y la estructura de la base de datos. Añadir el resto de la información de a una por vez sería tedioso. Vas a crear un script que lo haga por ti. Te recomiendo "dividir" la terminal para esta parte. Puedes hacerlo haciendo clic en el menú "hamburguesa" en la parte superior izquierda de la ventana, yendo al menú "Terminal" y haciendo clic en "Dividir terminal". Una vez que hayas hecho eso, utiliza el comando touch para crear un archivo llamado insert_data.sh en la carpeta de tu proyecto.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2046.png)

Debes tener dos terminales abiertas. Una conectada a PostgreSQL y otra para ingresar comandos de terminal. En la de comandos de terminal, usa el comando chmod con el indicador +x para otorgarle permisos de ejecución de scripts nuevos.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2047.png)

Abre el nuevo archivo y agrega un "shebang" que use bash en la parte superior. Se verá así: #!/bin/bash.

Un shebang en bash es una secuencia de caracteres (`#!`) seguida de la ruta del intérprete que se debe utilizar para ejecutar el script. En el caso de bash, se usa `#!/bin/bash`. Esta línea debe estar en la parte superior del script y le indica al sistema operativo qué intérprete utilizar para ejecutar el archivo. Por ejemplo, `#!/bin/bash` le dice al sistema que use el shell bash para ejecutar el script.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2048.png)

Below that, add a single line comment with the text, `Script to insert data from courses.csv and students.csv into students database`.

Lo hacemos con # (comentario indicado)

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2049.png)

Primero, debes agregar toda la información del archivo courses.csv, ya que necesitas el major_id para insertar la información del estudiante. cat es un comando de terminal para imprimir el contenido de un archivo. Aquí tienes un ejemplo: cat <filename>. Debajo del comentario que agregaste, úsalo para imprimir courses.csv.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2050.png)

Ejecute el script para ver si se imprime el contenido del archivo.

Lo hacemos en la terminal de bash con el comando ./insert_data.sh

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2051.png)

Funcionó. En lugar de imprimir el contenido, puedes canalizar esa salida a un bucle while para poder recorrer las filas una a la vez. Se ve así:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2052.png)

Cada nueva línea se leerá en las variables MAJOR y COURSE. Agregue lo anterior a su comando cat. En el área STATEMENTS, use echo para imprimir la variable MAJOR.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2053.png)

Run the script to see if it worked.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2054.png)

Está en bucle, pero la variable MAJOR solo se establece en la primera palabra. Hay una variable IFS predeterminada en bash. IFS significa "Separador de campo interno". 

Véalo con declare -p IFS.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2055.png)

Esta variable se utiliza para determinar los límites de las palabras. Por defecto, se utilizan espacios, tabulaciones y nuevas líneas. Por este motivo, la variable MAJOR se estableció solo en la primera palabra de cada línea de los datos. Entre los comandos while y read, establezca IFS en una coma de la siguiente manera: IFS=, “

Aguegué la IFS=“,” en el archivo insert_data.sh

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2056.png)

Ahora debería usar la coma en los datos para separar palabras en lugar de espacios. Ejecute el script nuevamente para ver si funciona.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2057.png)

Parece que funcionó. Imprime todo major, incluido el espacio. Imprime la variable COURSE en la misma línea en la que imprimes MAJOR para asegurarte de que todo funciona.

Para hacer el requerimiento sólo agregué $COURSE en la lnea donde dice ECHO

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2058.png)

Ejecute el script nuevamente para comprobarlo.

Para ejecutar el archivo  se hace con el comando : ./insert_data.sh

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2059.png)

Bien, tu bucle está funcionando. Puedes usar las variables MAJOR y COURSE para acceder a la especialidad o al curso cuando necesites insertar datos o consultar la base de datos. Elimina la línea echo para que puedas saber qué hacer a continuación.

Ayuda a planificar lo que quieres que suceda. Para cada bucle, deberás agregar la especialidad a la base de datos si aún no está allí. Lo mismo para el curso. Luego, agrega una fila a la tabla majors_courses. Agrega estos comentarios de una sola línea en tu bucle en este orden: obtener major_id, si no se encuentra, insertar especialidad, obtener nueva major_id, obtener course_id, si no se encuentra, insertar curso, obtener nueva course_id, insertar en majors_courses.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2060.png)

El resultado de mi script se ve asi:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2061.png)

Usaste el comando psql para iniciar sesión e interactuar con la base de datos. Puedes usarlo para ejecutar un solo comando y salir. Encima de tu bucle, agrega una variable PSQL que se vea así: PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c". Esto te permitirá consultar tu base de datos desde tu script. Las partes importantes son el nombre de usuario, el nombre de la base de datos y el indicador -c que es para ejecutar un solo comando y salir. El resto de los indicadores son para formatear.

la variable se agregó en la linea 4:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2062.png)

Ahora, puedes consultar tu base de datos usando la variable PSQL de esta manera: $($PSQL "<query_here>"). El código entre paréntesis se ejecutará en un subshell, que es un proceso bash independiente. Debajo del comentario get major_id en tu bucle, crea una variable MAJOR_ID. Establécela igual al resultado de una consulta que obtenga el major_id del MAJOR actual en el bucle. Asegúrate de poner tu variable MAJOR entre comillas simples.

Ahora mi script se verá así:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2063.png)

Debajo de la variable que acabas de crear, usa echo para imprimirla para que puedas ver su valor cuando ejecutes el script.

Con lo anterior se verá así:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2064.png)

Ejecute el script para ver qué sucede.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2065.png)

Entonces, revisó cada una de major del archivo CSV e intentó encontrar major_id para cada una de ellas en la base de datos. Parece que solo encontró la que insertó manualmente antes. El resto estaban vacíos. Debajo de su primer comentario if not found, agregue una condición if que verifique si la variable MAJOR_ID está vacía. Puede hacerlo con esta prueba: [[ -z $MAJOR_ID ]]. Coloque los siguientes dos comentarios en el área de declaraciones del if.

Las líneas destacadas fueron las insertadas:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2066.png)

El bucle se ejecutará de esta manera siempre que no se encuentre una especialidad. Aquí, querrás insertar la especialidad y luego obtener el nuevo ID. Necesitarás el ID para insertar datos en la tabla majors_courses más adelante. 

Debajo del comentario de inserción de la especialidad, crea una variable INSERT_MAJOR_RESULT. Establece su valor en una consulta que inserte la especialidad actual en la base de datos. No olvides usar comillas simples alrededor del valor.

hints:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2067.png)

El bucle se ejecutará de esta manera siempre que no se encuentre una especialidad. Aquí, querrás insertar la especialidad y luego obtener el nuevo ID. Necesitarás el ID para insertar datos en la tabla majors_courses más adelante. Debajo del comentario de inserción de la especialidad, crea una variable INSERT_MAJOR_RESULT. Establece su valor en una consulta que inserte la especialidad actual en la base de datos. No olvides usar comillas simples alrededor del valor.

La línea destacada es la que se agregó al script:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2068.png)

Debajo de la variable que acaba de crear, use echo para imprimirla.

1. Add `echo $INSERT_MAJOR_RESULT` right below where you created it

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2069.png)

En lugar de ejecutar todos los datos del archivo CSV, debería crear algunos datos de prueba. En la terminal, utilice el comando copy (cp) para copiar courses.csv en un nuevo archivo llamado courses_test.csv.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2070.png)

En el nuevo archivo, elimine todos los datos, excepto las primeras cinco líneas. Asegúrese de que haya una sola línea vacía en la parte inferior.

En el nuevo archivo creado solo deje las primeras 5 lineas como indican.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2071.png)

De regreso en el script insert_data.sh, cambie el comando cat para recorrer el archivo de prueba en lugar del archivo completo.

1. Change your `cat` command to `cat courses_test.csv` instead of `cat courses.csv`

El cambio se realizó en la linea 5 destacada:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2072.png)

Ejecute el script. Analizará los datos de prueba e insertará una especialidad en la base de datos cada vez que no encuentre ninguna ya existente e imprimirá las variables MAJOR_ID e INSERT_MAJOR_RESULT.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2073.png)

Parece que encontró un ID que ya estaba en la base de datos dos veces e insertó tres elementos nuevos en la base de datos. Ya no es necesario imprimir el ID, así que elimine la línea echo $MAJOR_ID.

se elimina echo en la línea destacada según lo requerido:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2074.png)

En el indicador de psql, use SELECT para ver todos los datos de la tabla de especialidades para ver qué agregó el script.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2075.png)

Olvidé que insertaste la Administración de base de datos anteriormente. El script se ejecutó e insertó major desde la línea superior del archivo. Luego agregó los otros dos que aún no estaban allí. Puedes usar TRUNCATE para eliminar todos los datos de una tabla. En el indicador de psql, intenta eliminar todos los datos en la tabla majors ingresando TRUNCATE majors;

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2076.png)

Dice que "no se puede truncar una tabla a la que se hace referencia en una restricción de clave externa". Las tablas students y majors_courses utilizan el major_id de majors como clave externa. Por lo tanto, si desea eliminar los datos de majors, debe eliminar los datos de esas dos tablas al mismo tiempo. Utilice TRUNCATE para eliminar los datos de esas tres tablas. Separe las tablas con comas.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2077.png)

View all the data in the `majors` table to make sure it's empty.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2078.png)

Looks like it worked. View all the data in the `majors_courses` table to see if that one is empty.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2079.png)

Verifica la tabla de estudiantes:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2080.png)

Verifica la tabla de courses:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2081.png)

Debería quedar una entrada allí. Utilice TRUNCATE para eliminar todos los datos de la tabla courses. Deberá truncar todas las tablas que utilicen una columna de esta como clave externa al mismo tiempo.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2082.png)

para ver las tablas asociadas utilise el comando \d para ver las relaciones de la tabla courses:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2083.png)

Debería quedar una entrada allí. Utilice TRUNCATE para eliminar todos los datos de la tabla courses. Deberá truncar todas las tablas que utilicen una columna de esta como clave externa al mismo tiempo.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2084.png)

Verifica la tabla de courses nuevamente:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2085.png)

Ahora la base de datos está completamente vacía. Ejecute el script nuevamente para ver qué se inserta cuando la base de datos está vacía.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2086.png)

Insertó cuatro en ese momento. En el indicador de psql, visualice todos los datos en la tabla majors:

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2087.png)

No querrás agregar la primera línea del archivo CSV a la base de datos, ya que son solo títulos. En tu secuencia de comandos, agrega una condición if en la parte superior de tu bucle que verifique si $MAJOR != major. Coloca todo el código y los comentarios existentes en tu bucle en su área de declaraciones para que solo haga algo que no sea la primera línea.

Se agrega la línea destacada

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2088.png)

En el indicador de psql, utilice TRUNCATE para eliminar todos los datos de la tabla de majors

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2089.png)

View all the data in `majors` table to make sure it's empty.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2090.png)

Run the script to make sure it's not adding the first line anymore

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2091.png)

Solo se mostraron tres inserciones, lo cual es una buena señal. Vea todos los datos en la tabla de las principales para asegurarse de que sean tres las que desea.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2092.png)

Hay tres especialidades únicas en los datos de prueba. Esas fueron las tres que se agregaron a la base de datos, por lo que parece que funciona. Borre la línea donde imprime INSERT_MAJOR_RESULT.

se borra la llinea destacada donde estaba el cmando echo 

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2093.png)

Quieres un mensaje más agradable cuando se inserta algo para que sea más informativo. Debajo de la variable INSERT_MAJOR_RESULT, agrega una declaración if que verifique si la variable es igual a INSERT 0 1, que era lo que estaba imprimiendo. Usa echo para imprimir Inserted into majors, $MAJOR en el área de declaraciones del if.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2094.png)

En el indicador de psql, trunque nuevamente la tabla majors para poder ejecutar el script y ver el resultado.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2095.png)

Check to make sure the table is empty. Then, run the script.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2096.png)

Está empezando a tomar forma. Debajo del comentario para obtener el nuevo major_id, configure la variable MAJOR_ID en una consulta que obtenga el nuevo major_id de la base de datos.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2097.png)

De esta forma, el script insertará las carreras correctamente. A continuación, se encuentran los cursos. Serán los mismos pasos que para las carreras. Debajo del comentario get course_id, agrega una variable COURSE_ID que obtenga el course_id de la base de datos. Recuerda que tu variable COURSE tendrá el curso actual en el bucle.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2098.png)

Es lo mismo que las especialidades, por lo que debajo del segundo comentario "si no se encuentra", agrega una declaración "if" que verifique si la consulta estaba vacía para que puedas insertar el curso si es necesario. Coloca los comentarios "insert course" y "get new course_id" existentes en el área de declaraciones del "if".

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%2099.png)

Debajo del comentario de inserción del curso, cree una variable INSERT_COURSE_RESULT que inserte el curso en la base de datos.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20100.png)

La variable debe ser INSERT 0 1 nuevamente si se inserta algo. Debajo de la variable que acaba de crear, agregue una condición if que verifique si lo es e imprima Inserted into courses, $COURSE using echo en su área de declaraciones.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20101.png)

In the psql prompt, truncate the data from the `majors` table so you can run the script again.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20102.png)

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20103.png)

Parece que funcionó. Los datos de prueba tienen tres cursos únicos y se agregaron tres a la base de datos. Vea los datos en la tabla de cursos para asegurarse de que sean correctos.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20104.png)

Excelente. En lugar de eliminar manualmente los datos cada vez que desee ejecutar el script, agregue el comando para que lo haga por usted. Cerca de la parte superior del archivo, debajo de la variable PSQL, use echo para consultar la base de datos. En la consulta, trunque las cuatro tablas en este orden: estudiantes, carreras, cursos, carreras_especialidades.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20105.png)

Run the script to see if it works.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20106.png)

Genial. Eso lo hace más fácil. Debajo del comentario de obtención del nuevo course_id, establece el COURSE_ID en el course_id recién insertado.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20107.png)

Una cosa más para agregar a este archivo. Debajo del comentario de cursos insert into majors_courses, crea una variable INSERT_MAJORS_COURSES_RESULT. Úsala junto con las variables MAJOR_ID y COURSE_ID que creaste para insertar una fila en la tabla majors_courses. Asegúrate de que la consulta tenga primero la columna major_id. Además, no necesitarás comillas alrededor de los valores de los identificadores.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20108.png)

Debajo de la variable que acabas de crear, agrega una condición if que verifique si es igual a INSERT 0 1 como las demás. En su área de declaraciones, usa echo para imprimir Inserted into majors_courses, $MAJOR : $COURSE.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20109.png)

Ejecute el script. Las tablas se truncarán y luego el programa deberá realizar el bucle y agregar todos los datos de courses_test.csv a las tres tablas de la base de datos.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20110.png)

Looks like it works. You better look around to make sure. View the data in the `majors` table.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20111.png)

chequea la tabla courses

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20112.png)

Por último, mira los datos en la tabla majors_courses. Debería haber cuatro filas.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20113.png)

Bien, esa parte del script está lista. A continuación, debes agregar todo lo que se encuentra en el archivo students.csv. Crea algunos datos de prueba nuevamente. En la terminal, usa el comando copy para copiar students.csv en un archivo llamado students_test.csv.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20114.png)

En el archivo students_test.csv, elimine todo excepto las primeras cinco líneas, como hizo en el otro archivo de prueba. Asegúrese de que haya una línea vacía en la parte inferior nuevamente.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20115.png)

Quiere recorrer toda esta información como lo hizo para el otro archivo CSV. El proceso es el mismo. Debajo del bucle existente, use cat para imprimir el nuevo archivo de prueba. Envíe los resultados a un bucle while, configurando IFS nuevamente en una coma y luego use read para crear las variables FIRST, LAST, MAJOR y GPA a partir de los datos. En el bucle, use echo para imprimir la variable FIRST.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20116.png)

Ejecute el script para ver si imprime correctamente la variable FIRST (first_name). Tomará un segundo, ya que debe pasar por el primer bucle.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20117.png)

Funciona 😅 Imprime el primer elemento de cada fila del archivo CSV. Está imprimiendo la primera línea nuevamente, tendrás que encargarte de eso. Primero, elimina la línea de eco.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20118.png)

Agregue una condición if al bucle que verifique si la variable FIRST no es igual a first_name, de modo que no haga nada en la primera línea del archivo. No coloque nada en el área de declaraciones por ahora.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20119.png)

Todas las columnas del archivo CSV se pueden insertar directamente en la base de datos, excepto la de la major. Para ello, deberá obtener nuevamente el major_id. También hay algunos valores nulos, por lo que deberá utilizar null si no se encuentra el major_id. Agregue cuatro comentarios de una sola línea en su bucle; obtenga major_id, si no se encuentra, configúrelo como null e inserte student en ese orden.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20120.png)

Debajo del nuevo comentario get major_id, configure la variable MAJOR_ID en una consulta que obtenga el major_id para la especialidad de los estudiantes actuales.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20121.png)

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20122.png)

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20123.png)

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20124.png)

Al observar los datos de prueba, se encontró el ID de todos ellos, excepto el valor nulo. Debajo del comentario "si no se encuentra" más reciente, agregue un "if" que verifique si la variable está vacía. Coloque el comentario "Configurar como nulo" en su área de declaraciones.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20125.png)

Cuando vaya a insertar los datos del estudiante, deberá utilizar MAJOR_ID si se encuentra o null si no lo encuentra. Debajo del comentario de configuración nula, configure la variable MAJOR_ID como null para poder usarla para insertar los datos.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20126.png)

Mueva la línea echo $MAJOR_ID debajo de la declaración if para que pueda ejecutar el script y ver el valor de la variable si se encuentra o no el major_id.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20127.png)

run the script

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20128.png)

Está bien, eso debería funcionar para insertar al estudiante. Borra la línea echo $MAJOR_ID

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20129.png)

Una última cosa para agregar. En el indicador de psql, visualice los detalles de la tabla de estudiantes para que pueda ver qué columnas agregar.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20130.png)

Necesitará configurar las cuatro columnas al agregar la información del estudiante. Todas ellas excepto student_id. Debajo del comentario de inserción del estudiante, cree una variable INSERT_STUDENT_RESULT que agregue al estudiante a la base de datos. Agregue las columnas en el orden en que aparecen en los datos y asegúrese de poner solo las dos columnas VARCHAR entre comillas simples.

INSERT_STUDENT_RESULT=$($PSQL "INSERT INTO students(first_name, last_name, major_id, gpa) VALUES('$FIRST', '$LAST', $MAJOR_ID, $GPA)")

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20131.png)

Debajo de la variable que acabas de crear, agrega una declaración if que verifique si es igual a INSERT 0 1 como las demás. Si lo es, usa echo para imprimir Inserted into students, <first_name> <last_name>.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20132.png)

Run the script to see if the students are getting added.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20133.png)

Creo que está funcionando. Vea todos los datos en la tabla de estudiantes para asegurarse de que coincidan con el archivo CSV.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20134.png)

Excelente. Se agregaron todos los estudiantes de los datos de la prueba. Es hora de probarlo con los archivos originales. Cambie la línea cat courses_test.csv para usar nuevamente el archivo original.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20135.png)

A continuación, cambie la línea cat students_test.csv para utilizar también el archivo original.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20136.png)

Run the script

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20137.png)

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20138.png)

Eso estuvo genial. Mira todos los datos en la tabla de estudiantes para ver qué obtuviste al final.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20139.png)

31 filas. Esa es la cantidad que hay en el archivo CSV. Perfecto. A continuación, consulte la tabla de majors.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20140.png)

7 filas. Debe haber 7 carreras únicas en el archivo CSV. Ver lo que hay en la tabla de cursos.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20141.png)

Parece que hay 17 cursos únicos en el archivo CSV. Por último, vea los datos en majors_courses. Debería tener la misma cantidad de filas que el archivo CSV.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20142.png)

28 filas, lo mismo que el archivo CSV. Creo que todos los datos se agregaron correctamente. Ya no necesitas los archivos de prueba. En la terminal, usa el comando list para verificar qué archivos hay en la carpeta de tu proyecto.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20143.png)

Utilice el comando eliminar (rm) para eliminar el archivo students_test.csv.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20144.png)

Use the same command to delete the `courses_test.csv` file.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20145.png)

List the contents of the folder again to make sure they're gone.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20146.png)

La base de datos está terminada por ahora. Lo último que vas a hacer es crear un "volcado" de la misma. El comando pg_dump puede hacer eso por ti. Usa el indicador --help con el comando para ver qué puede hacer.

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20147.png)

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20148.png)

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20149.png)

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20150.png)

![Untitled](UPSK-SQL001-sql-student-database%203415c419c1a549c3bf226b952d76f5bb/Untitled%20151.png)
