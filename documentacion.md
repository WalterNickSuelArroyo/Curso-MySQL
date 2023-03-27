# 1. INTRODUCCIÓN
## 1. INTRODUCCIÓN AL CURSO:
MySQL es la mas popular

# 2. CONCEPTOS DE BASES DE DATOS
## 2. QUE SON LAS BASES DE DATOS
Una base de datos es una coleccion de datos ordenados y organizados, de tal manera que nos permitan acceder rapidamente y facilmente a ellos. Ejemplo de BD es la guia telefonica.

## 3. CONCEPTO DE MOTORES DE BASES DE DATOS
Un motor de base de datos es un software que se encarga de administrar y gestionar el acceso a los datos almacenados en una base de datos.

Los motores de bases de datos pueden clasificarse en dos tipos principales:

Bases de datos relacionales: estos motores de base de datos utilizan el modelo de datos relacional, que se basa en tablas con filas y columnas para almacenar los datos. Ejemplos de motores de bases de datos relacionales son MySQL, PostgreSQL, Oracle, SQL Server, SQLite, entre otros.

Bases de datos no relacionales: estos motores de base de datos utilizan modelos de datos no relacionales, como el modelo de documentos, el modelo clave-valor o el modelo de grafos, para almacenar los datos. Ejemplos de motores de bases de datos no relacionales son MongoDB, Redis, Cassandra, Neo4j, entre otros.

## 4. CONCEPTO DE TABLAS
Una tabla es una estructura de datos que se utiliza para almacenar información en forma de filas y columnas. Cada tabla está diseñada para contener información sobre un conjunto específico de objetos o entidades, y cada fila de la tabla representa una instancia o registro de esa entidad.

## 5. CONCEPTOS DE CAMPOS
En una base de datos, un campo es la unidad básica de información que se almacena en una tabla. Los campos representan las diferentes propiedades o atributos de una entidad, como el nombre, la dirección, la fecha de nacimiento, el género, etc.

Cada campo se representa por una columna en la tabla, y cada fila de la tabla representa una instancia de la entidad con sus respectivos valores de campo. Por ejemplo, si tenemos una tabla de "Clientes", cada fila de la tabla representará a un cliente diferente, y las columnas de la tabla representarán sus atributos o campos, como el nombre, la dirección, el número de teléfono, el correo electrónico, etc.

Cada campo en una base de datos tiene un tipo de datos asociado, que define el tipo de valor que se puede almacenar en ese campo, como números, fechas, cadenas de texto, etc. Además, cada campo puede tener restricciones de integridad para garantizar que los datos almacenados sean válidos y consistentes. Por ejemplo, se pueden establecer restricciones para asegurar que un campo no pueda estar vacío, o que un campo solo pueda contener valores únicos.

## 6. CONCEPTO DE INDICES
Los índices son estructuras de datos que se utilizan para mejorar la eficiencia de las consultas y operaciones en una base de datos, permitiendo acceder rápidamente a los registros que cumplen con ciertas condiciones. Los índices se crean en una o varias columnas de una tabla y pueden ser útiles en grandes bases de datos, pero deben ser utilizados con cuidado.

**TIPOS DE INDICES**

**Clave primaria (Primary Key)**: Es una columna o conjunto de columnas que identifica de manera única cada registro en una tabla. Cada tabla debe tener una clave primaria, que se utiliza para garantizar que no haya registros duplicados y para mejorar la velocidad de las búsquedas en la tabla. La clave primaria debe cumplir con ciertas características, como ser única, no nula y estable, es decir, que no cambie con el tiempo.

**Clave única (Unique Key)**: Es similar a la clave primaria en el sentido de que identifica de manera única los registros en una tabla. La diferencia es que una tabla puede tener varias claves únicas, mientras que solo puede tener una clave primaria. Las claves únicas se utilizan para garantizar que no haya registros duplicados en una o varias columnas de una tabla.

**Clave (Key)**: Es una columna o conjunto de columnas que se utiliza para acelerar la búsqueda de registros en una tabla. A diferencia de la clave primaria y la clave única, una clave puede contener valores duplicados. Las claves se utilizan para mejorar la velocidad de las búsquedas en una tabla, pero no garantizan la unicidad de los registros.

# BASE DE DATOS EN MYSQL
## 7. QUE ES MYSQL 
MySQL es un sistema de gestión de bases de datos relacionales (RDBMS) muy popular y ampliamente utilizado. Fue desarrollado originalmente por MySQL AB, que fue adquirida por Sun Microsystems y posteriormente por Oracle Corporation. MySQL es un software libre y de código abierto, lo que significa que se puede descargar, utilizar y modificar de forma gratuita.

## 8. ACLARACIONES SOBRE LA INSTALACION DE MYSQL
## 9. INSTALANDO MYSQL
## 10. INSTALAR XAMPP SE TE HA FALLADO LA INSTALACION DE MYSQL
## 11. INSTALANDO HEIDISQL EN MI PC
## 12. CONECTANDO AL SERVIDOR DE BASE DE DATOS CON HEIDISQL
## 13. CREANDO NUESTRA PRIMERA BASE DE DATOS
Para crear una base de datos en HeidiSQL damos clic derecho en local -> crear nuevo -> Base de Datos
## 14. CREANDO TABLAS Y CAMPOS