# UPSK-SQL001-sql-student-database

## psql Login

1. Primero accedemos con **echo sql hello**
2. Luego nos conectamos a la base de datos con **psql --username=freecodecamp --dbname=postgres**
3. listamos las bases de datos con el comando **\l**
## Crear Base de Datos : Students
1. La creamos con el siguiente comando : CREATE DATABASE <database_name>;
4. Creamos la base de datos **students**  con el comando **CREATE DATABASE students**
5. Verificamos que nuestra base de datos haya sido creada con el comando : **/l**
6. Nos conectamos a la base de datos creada con el comando **\c  + nombre de la basede datos** 

## Crear tablas Students, majors, courses, majors_courses:
1. La creamos con el comando **CREATE TABLE students();**
2. La segunda tabla será para cada especialización única que aparece en los datos.Crea una tabla llamada majors.
3. La creamos de la misma manera que anteriormente
4. La tercera tabla se llamará **courses**
5. La creamos de la misma manera
6. La tabla final será una tabla de unión para las especialidades y cursos. Créelo con el nombre **majors_courses.**
7. Utilice el comando de acceso directo de visualización para ver sus tablas y asegurarse de que está satisfecho con ellas.
8. Debemos usar el comando **\d**

## Crear columna en la tabla students:

Sobre las columnas. El archivo Students.csv tiene cuatro campos; creará una columna para cada uno de ellos, así como una columna de ID. Agregue una columna a la tabla de estudiantes llamada **Student_id**. Dale un tipo de SERIAL para que incremente automáticamente y conviértelo en CLAVE PRIMARIA.

* ALTER TABLE students ADD COLUMN student_id SERIAL PRIMARY KEY;

 La primera columna en Students.csv es **first_name.** Agregue una columna a la tabla de estudiantes con ese nombre. 2.2.Conviértalo en un tipo de VARCHAR(50) y asígnele la restricción NOT NULL.

* ALTER TABLE students ADD COLUMN first_name VARCHAR(50) NOT NULL;

 La siguiente columna de datos es last_name. Agréguela a la tabla students. Asígnele el mismo tipo de datos y la misma longitud máxima que first_name y asegúrese de que tenga la restricción NOT NULL.

* ALTER TABLE students ADD COLUMN last_name VARCHAR(50) NOT NULL;

La siguiente columna es para especialidad(major). Dado que tendrá cada especialidad en otra tabla, esta columna será una clave externa que la referencia. Cree una columna en la tabla de estudiantes llamada major_id y asígnele un tipo de datos INT por ahora. Volverá y establecerá la clave externa más tarde.

* ALTER TABLE students ADD COLUMN major_id INT;

Crea la última columna, gpa. Los datos del CSV muestran que son decimales con una longitud de 2 y que hay un número a la derecha del decimal. Asígnale un tipo de datos de NUMERIC(2,1).

* ALTER TABLE students ADD COLUMN gpa NUMERIC(2,1);

Utilice el comando de acceso directo para mostrar los detalles de la tabla de estudiantes para asegurarse de que le guste.
Para eso usamos **\d nombredelatabla**

## Creación de columnas para tabla majors

Aún falta la clave externa (forent key). A continuación, completemos la tabla de claves principales. Agreguemos una columna major_id. Conviértala en un tipo SERIAL y la CLAVE PRINCIPAL para esta tabla.

* ALTER TABLE majors ADD COLUMN major_id SERIAL PRIMARY KEY;

Esta tabla solo tendrá otra columna para el nombre de la especialidad(MAJOR). 
Agregue una columna llamada especialidad(MAJOR). Conviértala en un VARCHAR con una longitud máxima de 50 y asígnele la restricción NOT NULL.

* ALTER TABLE majors ADD COLUMN major VARCHAR(50) NOT NULL;

1. Consulta los detalles de la tabla de las principales carreras para asegurarte de que te gusta.
2. para eso usamos el comando **\d nombre_de_tabla**

## Create major_id foreign key
* ALTER TABLE students ADD FOREIGN KEY(major_id) REFERENCES majors(major_id);
1. Vea los detalles de la tabla students otra vez para asegurarte de que la key esta ahí
2. para eso usamos el comando **\d nombre de la tabla**

## Creación de  course_id Column
1. A continuación, está la tabla de courses. Añádele una columna course_id. Asígnale un tipo SERIAL y conviértela en la clave principal.

* ALTER TABLE courses ADD COLUMN course_id SERIAL PRIMARY KEY;

2. Agregue una columna course a la tabla de courses que sea de tipo VARCHAR. Los nombres de los cursos son un poco más largos, por lo que debe darles una longitud máxima de 100. Además, asegúrese de que no pueda aceptar valores nulos.

* ALTER TABLE courses ADD COLUMN course VARCHAR(100) NOT NULL;

> Para borrar una columna con datos erroneos
> **ALTER TABLE nombre_tabla DROP COLUMN column_b**;

 Vea los detalles de la tabla de cursos para asegurarse de que se vea bien: Lo hacemos con el comando **\d courses**

Falta una tabla más. La tabla de unión majors_courses tendrá dos columnas, cada una de las cuales hace referencia a la clave principal de dos tablas relacionadas. Primero, agrégale una columna major_id. Por ahora, solo dale un tipo INT.

## Establezca major_id como Foreign Key
1. Establezca la columna major_id que acaba de crear como una clave externa (FOREIGN KEY) que haga referencia a la columna major_id de la tabla majors.

* ALTER TABLE students ADD FOREIGN KEY(major_id) REFERENCES majors(major_id);

2. Agregue la columna  course_id a la tabla majors_courses de tipo INT

* ALTER TABLE majors_courses ADD COLUMN course_id INT;
##  Establezca course_id como Foreign Key
Establezca su nueva columna course_id como una clave externa(FOREIGN KEY) que haga referencia a la otra columna course_id.

* ALTER TABLE majors_courses ADD FOREIGN KEY(course_id) REFERENCES courses(course_id);

Utilice el comando de acceso directo para mostrar los detalles de la tabla de estudiantes para asegurarse de que le guste.para eso usamos **\d nombredelatabla**

## Crear Clave Primaria Compuesta":
Falta algo. Esta tabla no tiene una clave principal. Los datos de courses.csv irán en esta tabla. Una única especialidad aparecerá en ella varias veces, y lo mismo con un curso. Por lo tanto, ninguno de ellos puede ser una clave principal. Pero nunca habrá una fila con los mismos dos valores que otra fila. Por lo tanto, las dos columnas juntas son únicas. Puede crear una clave principal compuesta que use más de una columna como un par único de esta manera: ALTER TABLE <table_name> ADD PRIMARY KEY(<column_name>, <column_name>); Agregue una clave principal compuesta a la tabla usando las dos columnas.
**Esto hace que no se pueda repetir los cursos y las especialidad , es decir no habrán filas duplicadas**
* ALTER TABLE majors_courses ADD PRIMARY KEY(major_id, course_id);
Verificar los detalles con **\d majors_courses**
Terminamos , ahora veamos las tablas que terminaste.

**Con el comando : \d**

El comando \d en SQL se utiliza para mostrar la estructura de las tablas, vistas, secuencias y otros objetos en la base de datos. Proporciona detalles sobre las columnas, su tipo de datos, restricciones y claves asociadas.

A continuación, puedes comenzar a agregar información. Dado que la tabla de estudiantes necesita un major_id, puedes agregar primero una especialidad. Consulta los detalles de la tabla majors para ver qué información espera.
La consulta se hace con el comando **\d majors**

## INSERT INTO majors
Solo necesita el nombre de una especialidad. El ID se agregará automáticamente. Agregue la primera especialidad del archivo courses.csv a la tabla de especialidades. Es un VARCHAR, así que asegúrese de poner el valor entre comillas simples.

Con esta sentencia agregamos info a la columna major de la tabla majors el valor Database Administration

* INSERT INTO majors(major) VALUES('Database Administration');

Utilice SELECT para ver todos los datos en la tabla de especialidades para asegurarse de que se insertaron correctamente.
* SELECT * FROM majors;

## INSERT INTO courses
1. Inserta el primer curso desde courses.csv en la tabla courses
* INSERT INTO courses(course) VALUES('Data Structures and Algorithms');
2. Mira todos los datos en la tabla courses , para asegurarse de que se hayan agregado
* SELECT * FROM courses

## INSERT INTO majors_courses
1. A continuación, puede agregar una fila a la tabla de uniones. Vea los detalles de la misma para ver qué espera.
Quiere un major_id y un course_id. Agregue una fila a majors_courses para la primera entrada en courses.csv.
* INSERT INTO majors_courses(major_id, course_id) VALUES(1, 1);
2. Vea todos los datos de la tabla que acaba de agregar.
* SELECT * FROM majors_courses;
Parece que se agregó la fila. Vea los detalles de la tabla de estudiantes para recordar qué espera y poder agregar el primer estudiante a la base de datos.
Con el comando : **\d students**

## touch insert_data.sh
type **touch insert_data.sh** in en la nueva terminal y presiona enter

##  chmod +x insert_data.sh
escribe **chmod +x insert_data.sh** en la nueva terminal y presiona enter

Debes tener dos terminales abiertas. Una conectada a PostgreSQL y otra para ingresar comandos de terminal. En la de comandos de terminal, usa el comando chmod con el indicador +x para otorgarle permisos de ejecución de scripts nuevos.
## Add shebang
Abre el nuevo archivo y agrega un "shebang" que use bash en la parte superior.
Se verá así: **#!/bin/bash.**

Un shebang en bash es una secuencia de caracteres (`#!`) seguida de la ruta del intérprete que se debe utilizar para ejecutar el script. En el caso de bash, se usa `#!/bin/bash`. Esta línea debe estar en la parte superior del script y le indica al sistema operativo qué intérprete utilizar para ejecutar el archivo. Por ejemplo, `#!/bin/bash` le dice al sistema que use el shell bash para ejecutar el script.

Abajo de eso, agrega una linea de comentario con el texto, `Script to insert data from courses.csv and students.csv into students database`.

Lo hacemos con:**# (comentario indicado)**

Primero, debes agregar toda la información del archivo courses.csv, ya que necesitas el major_id para insertar la información del estudiante. cat es un comando de terminal para imprimir el contenido de un archivo. Aquí tienes un ejemplo: cat <filename>. Debajo del comentario que agregaste, úsalo para imprimir courses.csv.
* cat courses.csv 
Ejecute el script para ver si se imprime el contenido del archivo.
* ./insert_data.sh
## Add while read
Funcionó. En lugar de imprimir el contenido, puedes canalizar esa salida a un bucle while para poder recorrer las filas una a la vez. Se ve así:
```
cat courses.csv | while read MAJOR COURSE
do
  <STATEMENTS>
done
```
Cada nueva línea se leerá en las variables MAJOR y COURSE. Agregue lo anterior a su comando cat. En el área STATEMENTS, use echo para imprimir la variable MAJOR.
```
cat courses.csv | while read MAJOR COURSE
do
  echo $MAJOR
done
```
Run the script to see if it worked.
* ./insert_data.sh

## declare -p IFS
Está en bucle, pero la variable MAJOR solo se establece en la primera palabra. Hay una variable IFS predeterminada en bash. IFS significa "Separador de campo interno". 

* tipee en la terminal declare -p IFS

Esta variable se utiliza para determinar los límites de las palabras. Por defecto, se utilizan espacios, tabulaciones y nuevas líneas. Por este motivo, la variable MAJOR se estableció solo en la primera palabra de cada línea de los datos. Entre los comandos while y read, establezca IFS en una coma de la siguiente manera: IFS=, “

* Aguegué la IFS=“,” en el archivo insert_data.sh
```
cat courses.csv | while IFS="," read MAJOR COURSE
do
  echo $MAJOR
done
```
Ahora debería usar la coma en los datos para separar palabras en lugar de espacios. Ejecute el script nuevamente para ver si funciona.
* ./insert_data.sh in the terminal and press enter

Parece que funcionó. Imprime todo major, incluido el espacio. Imprime la variable COURSE en la misma línea en la que imprimes MAJOR para asegurarte de que todo funciona.

Para hacer el requerimiento sólo agregué $COURSE en la línea donde dice ECHO
```
cat courses.csv | while IFS="," read MAJOR COURSE
do
  echo $MAJOR $COURSE
done
```
Ejecute el script nuevamente para comprobarlo.

Para ejecutar el archivo  se hace con el comando **: ./insert_data.sh**

Bien, tu bucle está funcionando. Puedes usar las variables MAJOR y COURSE para acceder a la especialidad o al curso cuando necesites insertar datos o consultar la base de datos. 
## Delete echo
Elimina la línea echo para que puedas saber qué hacer a continuación.

Ayuda a planificar lo que quieres que suceda. Para cada bucle, deberás agregar la especialidad a la base de datos si aún no está allí. Lo mismo para el curso. Luego, agrega una fila a la tabla majors_courses. Agrega estos comentarios de una sola línea en tu bucle en este orden: obtener major_id, si no se encuentra, insertar especialidad, obtener nueva major_id, obtener course_id, si no se encuentra, insertar curso, obtener nueva course_id, insertar en majors_courses.

El resultado de mi script se ve asi:
```
do
  # get major_id

  # if not found

  # insert major

  # get new major_id

  # get course_id

  # if not found

  # insert course

  # get new course_id

  # insert into majors_courses

done
```
## Agrega PSQL Variable
Usaste el comando psql para iniciar sesión e interactuar con la base de datos. Puedes usarlo para ejecutar un solo comando y salir. Encima de tu bucle, agrega una variable PSQL que se vea así: PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c". Esto te permitirá consultar tu base de datos desde tu script. Las partes importantes son el nombre de usuario, el nombre de la base de datos y el indicador -c que es para ejecutar un solo comando y salir. El resto de los indicadores son para formatear.

la variable se agregó en la linea 4:
* PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"
## Add MAJOR_ID
Ahora, puedes consultar tu base de datos usando la variable PSQL de esta manera: $($PSQL "<query_here>"). El código entre paréntesis se ejecutará en un subshell, que es un proceso bash independiente. Debajo del comentario get major_id en tu bucle, crea una variable MAJOR_ID. Establécela igual al resultado de una consulta que obtenga el major_id del MAJOR actual en el bucle. Asegúrate de poner tu variable MAJOR entre comillas simples.

* MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")

Debajo de la variable que acabas de crear, usa echo para imprimirla para que puedas ver su valor cuando ejecutes el script.

* echo $MAJOR_ID

Ejecute el script para ver qué sucede.

* ./insert_data.sh

## Aguega if -z MAJOR_ID
Entonces, revisó cada una de major del archivo CSV e intentó encontrar major_id para cada una de ellas en la base de datos. Parece que solo encontró la que insertó manualmente antes. El resto estaban vacíos. Debajo de su primer comentario if not found, agregue una condición if que verifique si la variable MAJOR_ID está vacía. Puede hacerlo con esta prueba: [[ -z $MAJOR_ID ]]. Coloque los siguientes dos comentarios en el área de declaraciones del if.
```
if [[ -z $MAJOR_ID ]]
then
  # insert major

  # get new major_id

fi
```
## Agrega INSERT_MAJOR_RESULT
El bucle se ejecutará de esta manera siempre que no se encuentre una especialidad. Aquí, querrás insertar la especialidad y luego obtener el nuevo ID. Necesitarás el ID para insertar datos en la tabla majors_courses más adelante. 

Debajo del comentario de inserción de la especialidad, crea una variable INSERT_MAJOR_RESULT. Establece su valor en una consulta que inserte la especialidad actual en la base de datos. No olvides usar comillas simples alrededor del valor.

* INSERT_MAJOR_RESULT=$($PSQL "INSERT INTO majors(major) VALUES('$MAJOR')")

El bucle se ejecutará de esta manera siempre que no se encuentre una especialidad. Aquí, querrás insertar la especialidad y luego obtener el nuevo ID. Necesitarás el ID para insertar datos en la tabla majors_courses más adelante. Debajo del comentario de inserción de la especialidad, crea una variable INSERT_MAJOR_RESULT. Establece su valor en una consulta que inserte la especialidad actual en la base de datos. No olvides usar comillas simples alrededor del valor.

Debajo de la variable que acaba de crear, use echo para imprimirla.
* echo $INSERT_MAJOR_RESULT


## cp courses.csv

En lugar de ejecutar todos los datos del archivo CSV, debería crear algunos datos de prueba. En la terminal, utilice el comando copy (cp) para copiar courses.csv en un nuevo archivo llamado courses_test.csv.

* cp courses.csv courses_test.csv

En el nuevo archivo, elimine todos los datos, excepto las primeras cinco líneas. Asegúrese de que haya una sola línea vacía en la parte inferior.

En el nuevo archivo creado solo deje las primeras 5 lineas como indican.

major,course
Database Administration,Data Structures and Algorithms
Web Development,Web Programming
Database Administration,Database Systems
Data Science,Data Structures and Algorithms

## Change to cat courses_test.csv

De regreso en el script insert_data.sh, cambie el comando cat para recorrer el archivo de prueba en lugar del archivo completo.

Change your `cat` command to `cat courses_test.csv` instead of `cat courses.csv`

* cat courses_test.csv | while IFS="," read MAJOR COURSE

Ejecute el script:
* ./insert_data.sh

 Analizará los datos de prueba e insertará una especialidad en la base de datos cada vez que no encuentre ninguna ya existente e imprimirá las variables MAJOR_ID e INSERT_MAJOR_RESULT.

## Delete echo MAJOR_ID

Parece que encontró un ID que ya estaba en la base de datos dos veces e insertó tres elementos nuevos en la base de datos. Ya no es necesario imprimir el ID, así que elimine la línea echo $MAJOR_ID.

## SELECT * FROM majors
En el indicador de psql, use SELECT para ver todos los datos de la tabla de especialidades para ver qué agregó el script.

* SELECT * FROM majors;

Olvidé que insertaste la Administración de base de datos anteriormente. El script se ejecutó e insertó major desde la línea superior del archivo. Luego agregó los otros dos que aún no estaban allí. Puedes usar TRUNCATE para eliminar todos los datos de una tabla. En el indicador de psql, intenta eliminar todos los datos en la tabla majors ingresando TRUNCATE majors;

* TRUNCATE majors;

Dice que "no se puede truncar una tabla a la que se hace referencia en una restricción de clave externa". Las tablas students y majors_courses utilizan el major_id de majors como clave externa. Por lo tanto, si desea eliminar los datos de majors, debe eliminar los datos de esas dos tablas al mismo tiempo. Utilice TRUNCATE para eliminar los datos de esas tres tablas. Separe las tablas con comas.

* TRUNCATE majors, students, majors_courses;

## SELECT * FROM majors
Verifica todos los datos de la tabla `majors, asegurese de que se encuentra vacía.

## SELECT * FROM majors_courses
Looks like it worked. View all the data in the `majors_courses` table to see if that one is empty.

* SELECT * FROM majors_courses

## SELECT * FROM students
Verifica la tabla de estudiantes:
* SELECT * FROM students;

## SELECT * FROM courses
Verifica la tabla de courses:
* SELECT * FROM courses;

## TRUNCATE courses, majors_courses
Debería quedar una entrada allí. Utilice TRUNCATE para eliminar todos los datos de la tabla courses. Deberá truncar todas las tablas que utilicen una columna de esta como clave externa al mismo tiempo.

* TRUNCATE courses, majors_courses;
para ver las tablas asociadas utilise el comando \d para ver las relaciones de la tabla courses:
## SELECT * FROM courses
Debería quedar una entrada allí. Utilice TRUNCATE para eliminar todos los datos de la tabla courses. Deberá truncar todas las tablas que utilicen una columna de esta como clave externa al mismo tiempo.

Verifica la tabla de courses nuevamente:
* SELECT * FROM courses;

##  ./insert_data.sh
Ahora la base de datos está completamente vacía.
Ejecute el script nuevamente para ver qué se inserta cuando la base de datos está vacía.
* ./insert_data.sh

## SELECT * FROM majors
Insertó cuatro en ese momento. En el indicador de psql, visualice todos los datos en la tabla majors:
* SELECT * FROM majors;

## Add if major
No querrás agregar la primera línea del archivo CSV a la base de datos, ya que son solo títulos. En tu secuencia de comandos, agrega una condición if en la parte superior de tu bucle que verifique si $MAJOR != major. Coloca todo el código y los comentarios existentes en tu bucle en su área de declaraciones para que solo haga algo que no sea la primera línea.
```
do
  if [[ $MAJOR != major ]]
  then
    # get major_id
    MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")

    # if not found
    if [[ -z $MAJOR_ID ]]
    then
      # insert major
      INSERT_MAJOR_RESULT=$($PSQL "INSERT INTO majors(major) VALUES('$MAJOR')")
      echo $INSERT_MAJOR_RESULT

      # get new major_id

    fi

    # get course_id

    # if not found

    # insert course

    # get new course_id

    # insert into majors_courses

  fi
done
```
# TRUNCATE majors CASCADE
En el indicador de psql, utilice TRUNCATE para eliminar todos los datos de la tabla de majors

* TRUNCATE majors, students, majors_courses;

Revise los datos de la tabla `majors` para asegurarse de que está vacía

* SELECT * FROM majors;

Ejecute el script
* ./insert_data.sh

## SELECT * FROM majors
Solo se mostraron tres inserciones, lo cual es una buena señal. Vea todos los datos en la tabla de las principales para asegurarse de que sean tres las que desea.

* SELECT * FROM majors

## Delete echo INSERT_MAJOR_RESULT
Hay tres especialidades únicas en los datos de prueba. Esas fueron las tres que se agregaron a la base de datos, por lo que parece que funciona. Borre la línea donde imprime INSERT_MAJOR_RESULT.

* Borrar :echo $INSERT_MAJOR_RESULT

## Add if INSERT_MAJOR_RESULT
Quieres un mensaje más agradable cuando se inserta algo para que sea más informativo. Debajo de la variable INSERT_MAJOR_RESULT, agrega una declaración if que verifique si la variable es igual a INSERT 0 1, que era lo que estaba imprimiendo. Usa echo para imprimir Inserted into majors, $MAJOR en el área de declaraciones del if.
```
if [[ $INSERT_MAJOR_RESULT == "INSERT 0 1" ]]
then
  echo "Inserted into majors, $MAJOR"
fi
```
## TRUNCATE majors CASCADE
En el indicador de psql, trunque nuevamente la tabla majors para poder ejecutar el script y ver el resultado.
* TRUNCATE majors, students, majors_courses;

Vea si esta vacía , ejecute el script: 
* ./insert_data.sh

## Add MAJOR_ID
Está empezando a tomar forma. Debajo del comentario para obtener el nuevo major_id, configure la variable MAJOR_ID en una consulta que obtenga el nuevo major_id de la base de datos.
* MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")

## Add COURSE_ID
De esta forma, el script insertará las carreras correctamente. A continuación, se encuentran los cursos. Serán los mismos pasos que para las carreras. Debajo del comentario get course_id, agrega una variable COURSE_ID que obtenga el course_id de la base de datos. Recuerda que tu variable COURSE tendrá el curso actual en el bucle.

* COURSE_ID=$($PSQL "SELECT course_id FROM courses WHERE course='$COURSE'")

## Agregue if -z COURSE_ID
Es lo mismo que las especialidades, por lo que debajo del segundo comentario "si no se encuentra", agrega una declaración "if" que verifique si la consulta estaba vacía para que puedas insertar el curso si es necesario. Coloca los comentarios "insert course" y "get new course_id" existentes en el área de declaraciones del "if".
```
if [[ -z $COURSE_ID ]]
then
  # insert course

  # get new course_id

fi
```
## Agregue INSERT_COURSE_RESULT
Debajo del comentario de inserción del curso, cree una variable INSERT_COURSE_RESULT que inserte el curso en la base de datos.

* INSERT_COURSE_RESULT=$($PSQL "INSERT INTO courses(course) VALUES('$COURSE')")

## Agregue if INSERT_COURSE_RESULT
La variable debe ser INSERT 0 1 nuevamente si se inserta algo. Debajo de la variable que acaba de crear, agregue una condición if que verifique si lo es e imprima Inserted into courses, $COURSE using echo en su área de declaraciones.
```
if [[ $INSERT_COURSE_RESULT == "INSERT 0 1" ]]
then
  echo "Inserted into courses, $COURSE"
fi
```
## TRUNCATE majors CASCADE

In the psql prompt, truncate the data from the `majors` table so you can run the script again.

* TRUNCATE majors, students, majors_courses;

## SELECT * FROM courses

Parece que funcionó. Los datos de prueba tienen tres cursos únicos y se agregaron tres a la base de datos. Vea los datos en la tabla de cursos para asegurarse de que sean correctos.
* SELECT * FROM courses;

## Add echo TRUNCATE tables
Excelente. En lugar de eliminar manualmente los datos cada vez que desee ejecutar el script, agregue el comando para que lo haga por usted. Cerca de la parte superior del archivo, debajo de la variable PSQL, use echo para consultar la base de datos. En la consulta, trunque las cuatro tablas en este orden: estudiantes, carreras, cursos, carreras_especialidades.
* echo $($PSQL "TRUNCATE students, majors, courses, majors_courses")

Ejecute el script:
* ./insert_data.sh

## Add COURSE_ID
Genial. Eso lo hace más fácil. Debajo del comentario de obtención del nuevo course_id, establece el COURSE_ID en el course_id recién insertado.

* COURSE_ID=$($PSQL "SELECT course_id FROM courses WHERE course='$COURSE'")

## Add INSERT_MAJORS_COURSES_RESULT
Una cosa más para agregar a este archivo. Debajo del comentario de cursos insert into majors_courses, crea una variable INSERT_MAJORS_COURSES_RESULT. Úsala junto con las variables MAJOR_ID y COURSE_ID que creaste para insertar una fila en la tabla majors_courses. Asegúrate de que la consulta tenga primero la columna major_id. Además, no necesitarás comillas alrededor de los valores de los identificadores.

* INSERT_MAJORS_COURSES_RESULT=$($PSQL "INSERT INTO majors_courses(major_id, course_id) VALUES($MAJOR_ID, $COURSE_ID)")

## Add if INSERT_MAJORS_COURSES_RESULT
Debajo de la variable que acabas de crear, agrega una condición if que verifique si es igual a INSERT 0 1 como las demás. En su área de declaraciones, usa echo para imprimir Inserted into majors_courses, $MAJOR : $COURSE.
```
if [[ $INSERT_MAJORS_COURSES_RESULT == "INSERT 0 1" ]]
then
  echo "Inserted into majors_courses, $MAJOR : $COURSE"
fi
```
Ejecute el script:
* ./insert_data.sh

Las tablas se truncarán y luego el programa deberá realizar el bucle y agregar todos los datos de courses_test.csv a las tres tablas de la base de datos.

## SELECT * FROM majors
Looks like it works. You better look around to make sure. View the data in the `majors` table.
* SELECT * FROM majors;

chequea la tabla courses:
* SELECT * FROM courses;

Por último, mira los datos en la tabla majors_courses. Debería haber cuatro filas.
* SELECT * FROM majors_courses;

## cp students.csv
Bien, esa parte del script está lista. A continuación, debes agregar todo lo que se encuentra en el archivo students.csv. Crea algunos datos de prueba nuevamente. En la terminal, usa el comando copy para copiar students.csv en un archivo llamado students_test.csv.

* cp students.csv students_test.csv

## Remove all but fours lines
En el archivo students_test.csv, elimine todo excepto las primeras cinco líneas, como hizo en el otro archivo de prueba. Asegúrese de que haya una línea vacía en la parte inferior nuevamente.

first_name,last_name,major,gpa
Rhea,Kellems,Database Administration,2.5
Emma,Gilbert,null,null
Kimberly,Whitley,Web Development,3.8
Jimmy,Felipe,Database Administration,3.7

## Agregue cat students_test.csv
Quiere recorrer toda esta información como lo hizo para el otro archivo CSV. El proceso es el mismo. Debajo del bucle existente, use cat para imprimir el nuevo archivo de prueba. Envíe los resultados a un bucle while, configurando IFS nuevamente en una coma y luego use read para crear las variables FIRST, LAST, MAJOR y GPA a partir de los datos. En el bucle, use echo para imprimir la variable FIRST.
```
cat students_test.csv | while IFS="," read FIRST LAST MAJOR GPA
do
  echo $FIRST
done
```
Ejecute el script para ver si imprime correctamente la variable FIRST (first_name). Tomará un segundo, ya que debe pasar por el primer bucle.

* ./insert_data.sh

Funciona 😅 Imprime el primer elemento de cada fila del archivo CSV. Está imprimiendo la primera línea nuevamente, tendrás que encargarte de eso. Primero, elimina la línea de eco.

Borre **echo $FIRST**

## Add if first_name
Agregue una condición if al bucle que verifique si la variable FIRST no es igual a first_name, de modo que no haga nada en la primera línea del archivo. No coloque nada en el área de declaraciones por ahora.
```
cat students_test.csv | while IFS="," read FIRST LAST MAJOR GPA
do
  if [[ $FIRST != "first_name" ]]
  then

  fi
done
```
## Agregue comments
Todas las columnas del archivo CSV se pueden insertar directamente en la base de datos, excepto la de la major. Para ello, deberá obtener nuevamente el major_id. También hay algunos valores nulos, por lo que deberá utilizar null si no se encuentra el major_id. Agregue cuatro comentarios de una sola línea en su bucle; obtenga major_id, si no se encuentra, configúrelo como null e inserte student en ese orden.
```
cat students_test.csv | while IFS="," read FIRST LAST MAJOR GPA
do
  if [[ $FIRST != "first_name" ]]
  then
    # get major_id

    # if not found

    # set to null

    # insert student

  fi
done
```
## Add MAJOR_ID
Debajo del nuevo comentario get major_id, configure la variable MAJOR_ID en una consulta que obtenga el major_id para la especialidad de los estudiantes actuales.

* MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")

## Add if -z MAJOR_ID
Al observar los datos de prueba, se encontró el ID de todos ellos, excepto el valor nulo. Debajo del comentario "si no se encuentra" más reciente, agregue un "if" que verifique si la variable está vacía. Coloque el comentario "Configurar como nulo" en su área de declaraciones.
```
if [[ -z $MAJOR_ID ]]
then
  # set to null
fi
```

## Set MAJOR_ID to null
Cuando vaya a insertar los datos del estudiante, deberá utilizar MAJOR_ID si se encuentra o null si no lo encuentra. Debajo del comentario de configuración nula, configure la variable MAJOR_ID como null para poder usarla para insertar los datos.
```
if [[ -z $MAJOR_ID ]]
then
  # set to null
  MAJOR_ID=null
fi
```
## Mueva echo MAJOR_ID
Mueva la línea echo $MAJOR_ID debajo de la declaración if para que pueda ejecutar el script y ver el valor de la variable si se encuentra o no el major_id.
* Mueva la línea sugerida debajo del final de la declaración if [[ -z $MAJOR_ID ]]

Run the script : **./insert_data.sh**
## Delete echo MAJOR_ID

Está bien, eso debería funcionar para insertar al estudiante. Borra la línea **echo $MAJOR_ID**

Una última cosa para agregar. En el indicador de psql, visualice los detalles de la tabla de estudiantes para que pueda ver qué columnas agregar.

* \d students

## Add INSERT_STUDENT_RESULT
Necesitará configurar las cuatro columnas al agregar la información del estudiante. Todas ellas excepto student_id. Debajo del comentario de inserción del estudiante, cree una variable INSERT_STUDENT_RESULT que agregue al estudiante a la base de datos. Agregue las columnas en el orden en que aparecen en los datos y asegúrese de poner solo las dos columnas VARCHAR entre comillas simples.

* INSERT_STUDENT_RESULT=$($PSQL "INSERT INTO students(first_name, last_name, major_id, gpa) VALUES('$FIRST', '$LAST', $MAJOR_ID, $GPA)")

## Add if INSERT_STUDENT_RESULT
Debajo de la variable que acabas de crear, agrega una declaración if que verifique si es igual a INSERT 0 1 como las demás. Si lo es, usa echo para imprimir Inserted into students, <first_name> <last_name>.
```
if [[ $INSERT_STUDENT_RESULT == "INSERT 0 1" ]]
then
  echo "Inserted into students, $FIRST $LAST"
fi
```
Ejecute el script para ver si los estudiantes fueron agregados:
* ./insert_data.sh

## SELECT * FROM students
Creo que está funcionando. Vea todos los datos en la tabla de estudiantes para asegurarse de que coincidan con el archivo CSV.
* SELECT * FROM students;

## Change to cat courses.csv
Excelente. Se agregaron todos los estudiantes de los datos de la prueba. Es hora de probarlo con los archivos originales. Cambie la línea cat courses_test.csv para usar nuevamente el archivo original.
* cat courses.csv | while IFS="," read MAJOR COURSE

## Change to cat students.csv
A continuación, cambie la línea cat students_test.csv para utilizar también el archivo original.
* cat students.csv | while IFS="," read FIRST LAST MAJOR GPA

Ejecute el script
* ./insert_data.sh

## SELECT * FROM students
Eso estuvo genial. Mira todos los datos en la tabla de estudiantes para ver qué obtuviste al final.
* SELECT * FROM students;

## SELECT * FROM majors
31 filas. Esa es la cantidad que hay en el archivo CSV. Perfecto. A continuación, consulte la tabla de majors.
* SELECT * FROM majors;

## SELECT * FROM courses
7 filas. Debe haber 7 carreras únicas en el archivo CSV. Ver lo que hay en la tabla de cursos.
* SELECT * FROM courses;

## SELECT * FROM majors_courses
Parece que hay 17 cursos únicos en el archivo CSV. Por último, vea los datos en majors_courses. Debería tener la misma cantidad de filas que el archivo CSV.
* SELECT * FROM majors_courses;

## ls
28 filas, lo mismo que el archivo CSV. Creo que todos los datos se agregaron correctamente. Ya no necesitas los archivos de prueba. En la terminal, usa el comando list (**ls**) para verificar qué archivos hay en la carpeta de tu proyecto.

## rm students_test.csv
Utilice el comando eliminar (rm) para eliminar el archivo students_test.csv.
* rm students_test.csv
## rm courses_test.csv
Usa el mismo comando para borrar el archivo `courses_test.csv`.

## ls
List the contents of the folder again to make sure they're gone.

##  pg_dump --help
**La base de datos está terminada por ahora.** Lo último que vas a hacer es crear un "volcado" de la misma. El comando pg_dump puede hacer eso por ti. Usa el indicador --help con el comando para ver qué puede hacer.

* pg_dump --help

## dump database
Este es el último paso. Hay varias opciones.
Ingresa **pg_dump --clean --create --inserts --username=freecodecamp students > students.sql** en la terminal para volcar la base de datos en un archivo students.sql. Esto guardará todos los comandos necesarios para reconstruirla. Echa un vistazo rápido al archivo cuando hayas terminado.

Versión en Notion : https://www.notion.so/UPSK-SQL001-sql-student-database-3415c419c1a549c3bf226b952d76f5bb?pvs=4
