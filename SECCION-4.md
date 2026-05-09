# SECCION 4: LENGUAJE SQL

## 24. Introduccion al lenguaje de base de datos

La clase es una introducción al lenguaje SQL (Structured Query Language o Lenguaje Estructurado de Consultas). El profesor explica que este lenguaje no es un bloque único, sino que está compuesto por cuatro grandes categorías o "mundos" de instrucciones, cada uno con un propósito específico dentro de la base de datos. El curso abordará los cuatro, pero comenzará enfocándose en la manipulación de datos.

El lenguaje SQL se divide en las siguientes cuatro categorías principales:

**1. DDL (Data Definition Language / Lenguaje de Definición de Datos)**

¿Para qué sirve? Se enfoca en la estructura y la "arquitectura" de la base de datos. No maneja los datos en sí, sino los "contenedores" donde irán esos datos.

¿Qué hace? Permite crear, modificar y eliminar objetos dentro del motor de la base de datos.

Objetos que maneja: Tablas, campos, índices, vistas, triggers (disparadores), stored procedures (procedimientos almacenados), eventos y funciones.

**2. DML (Data Manipulation Language / Lenguaje de Manipulación de Datos)**

¿Para qué sirve? Es el lenguaje que interactúa directamente con la información. (El instructor menciona que por aquí comenzará la parte práctica del curso).

¿Qué hace? Te permite hacer el día a día con los datos: ingresar nueva información, modificarla, borrarla y consultarla dentro de las tablas ya creadas.

**3. DCL (Data Control Language / Lenguaje de Control de Datos)**

¿Para qué sirve? Se encarga netamente de la seguridad del sistema.

¿Qué hace? Administra los usuarios que pueden entrar a la base de datos, otorgándoles permisos (qué pueden ver o hacer) o revocándoselos.

**4. TCL (Transaction Control Language / Lenguaje de Control de Transacciones)**

¿Para qué sirve? Gestiona las transacciones, que actúan como una capa de seguridad vital para operaciones complejas (como las de un banco).

¿Cómo funciona? Agrupa varias instrucciones bajo la premisa de "todo o nada". Si todas las operaciones se ejecutan correctamente, los cambios se guardan definitivamente (a esto se le llama Commit). Si alguna de las operaciones falla en el medio del proceso, el sistema deshace automáticamente todos los cambios para evitar errores o pérdidas de dinero/información (a esto se le llama Rollback).

Próximos pasos en el curso: El profesor concluye indicando que, aunque se verán las cuatro categorías a lo largo del curso (dejando permisos y transacciones para secciones más avanzadas), el siguiente capítulo arrancará directamente trabajando con DML (Manipulación de Datos).

## 25. Instrucción SELECT

En esta clase, el profesor nos introduce a la escritura de sentencias en SQL. Destaca que SQL es un lenguaje muy intuitivo, casi como dar instrucciones en inglés literal (palabras como UPDATE, INSERT, DELETE). El enfoque principal de la lección es la instrucción más importante y utilizada para interactuar con bases de datos: SELECT (Seleccionar), que nos permite extraer y visualizar los datos que necesitamos.

**La Estructura de una Consulta (Query)**

El profesor explica cómo se compone lógicamente una consulta en SQL. Aunque se verán en profundidad más adelante, menciona las partes principales que pueden conformarla:

    SELECT (¿Qué quiero consultar?): Es la instrucción principal. Aquí se definen qué columnas o campos específicos queremos traer.

    FROM (¿De dónde lo saco?): Es una palabra reservada obligatoria cuando interactuamos con tablas. Indica la tabla (o tablas) de donde el motor extraerá la información.

    WHERE (Filtros): Se usa para establecer condiciones (ej. "tráeme los productos donde el ID sea igual a 10"). Si no se usa, el motor traerá todos los registros.

    ORDER BY (Orden): Permite ordenar los resultados por uno o más campos, de forma ascendente o descendente.

    GROUP BY (Agrupamiento): Se utiliza para agrupar registros y obtener totales (ej. sumar el total vendido por cada producto).

    LIMIT: Sirve para restringir la cantidad de resultados que nos muestra la pantalla (ej. "solo muéstrame los primeros 10").

**Buenas Prácticas: El problema del Asterisco (*)**

El profesor hace mucho énfasis en la diferencia entre dos formas de usar el SELECT:

La forma rápida (Mala práctica): SELECT * FROM Productos

    - El asterisco (*) le dice al motor que traiga todas las columnas de la tabla.

    - ¿Por qué es malo? Exige trabajo innecesario al motor de la base de datos y consume más ancho de banda en la red (más bytes traficados). Si una tabla tiene 50 columnas y tú solo necesitas 3, estás desperdiciando muchísimos recursos. En entornos reales (especialmente en la nube), esto puede costar dinero extra y hacer que la aplicación sea lenta.

La forma correcta (Buena práctica): SELECT prod_id, prod_description, prod_precio FROM Productos

    - Consiste en escribir explícitamente y separados por comas solo los campos que necesitas.

    - Es más eficiente, rápido y demuestra que eres un buen administrador de bases de datos.

**Herramientas del Entorno (HeidiSQL)**

Finalmente, se dan un par de tips sobre el uso de la interfaz gráfica (HeidiSQL):

    - Panel de Ayuda: A la derecha, el programa ofrece una lista de funciones integradas (para fechas, matemáticas, promedios, sumas), una lista de palabras reservadas que no debes usar como nombres de columnas, y un historial de consultas.

    - Guardar el trabajo: Si creas una consulta muy compleja y útil, puedes ir a "Guardar" para almacenarla como un archivo .sql en tu computadora. Así, puedes armar tu propia biblioteca de consultas frecuentes y no perderlas al cerrar el programa.

## 26. Clausula WHERE

En esta lección, el profesor profundiza en la cláusula WHERE (Dónde), que funciona como el filtro principal en el lenguaje SQL. Destaca que esta herramienta no es exclusiva de las consultas (SELECT), sino que se usa en todas las instrucciones de manipulación de datos (DML) como UPDATE (actualizar) o DELETE (borrar) para asegurarnos de que solo estamos modificando o eliminando los registros correctos.

**1. Operadores Lógicos (AND, OR) y Paréntesis**

Para realizar filtros complejos, puedes encadenar múltiples condiciones utilizando operadores lógicos:

AND (Y): Exige que todas las condiciones se cumplan al mismo tiempo para que el registro se muestre. (Ej. Tráeme productos donde el precio sea mayor a 0 Y el ID del proveedor sea menor a 50).

OR (O): Permite que el registro se muestre si se cumple al menos una de las condiciones establecidas.

Paréntesis (): Al igual que en las matemáticas, los paréntesis se usan para agrupar condiciones y determinar en qué orden el motor de base de datos debe evaluarlas.

**2. Alias de Tablas (Buenas Prácticas)**

Un "alias" es un apodo temporal (usualmente una o dos letras) que se le asigna a una tabla en la instrucción FROM.

Ejemplo: En lugar de dejar solo FROM Productos, escribes FROM Productos p. Luego, puedes referirte a sus campos añadiendo un prefijo: p.prod_precio.

¿Por qué es útil? Cuando los sistemas crecen y debes consultar varias tablas al mismo tiempo, es muy común que distintas tablas tengan campos con el mismo nombre (por ejemplo, la columna ID). El alias le indica explícitamente al motor a qué tabla pertenece el ID que estás pidiendo, evitando errores de "ambigüedad". Además, usar alias activa el autocompletado en programas como HeidiSQL, acelerando tu escritura.

**3. Trabajando con Fechas**

Las bases de datos MySQL tienen una estructura muy estricta para interpretar el tiempo:

Formato estándar: AAAA-MM-DD (Año a cuatro dígitos, un guion, Mes a dos dígitos, un guion, Día a dos dígitos). Si es el día 2 de enero, se rellena con ceros: 2018-01-02.

Con hora (DateTime): Si el campo incluye la hora, el formato es AAAA-MM-DD HH:MM:SS.

Regla de oro: Todos los valores de fechas siempre deben ir encerrados entre comillas simples (' ').

**4. Funciones Nativas de Fecha**

SQL permite extraer partes específicas de un campo de fecha directamente dentro del filtro WHERE para hacer búsquedas precisas:

YEAR(campo_fecha): Si pones YEAR(ventas_fecha) = 2018, el motor ignorará el día y el mes, trayendo solo las ventas de ese año.

MONTH(campo_fecha): De igual forma, te permite buscar ventas de un mes específico (ej. MONTH(ventas_fecha) = 1 para enero), sin importar el año o día.

**5. El Operador BETWEEN (Entre)**

Es una instrucción muy eficiente para buscar información dentro de un rango de valores, evitando tener que escribir los signos de "mayor que" y "menor que" múltiples veces.

Sintaxis: WHERE ventas_fecha BETWEEN '2018-01-01' AND '2018-01-03'

Esta línea le pide al motor que devuelva todos los registros que existan entre esas dos fechas (incluyéndolas). Funciona exactamente igual para filtrar rangos numéricos, como precios o IDs.

Próximos pasos en el curso: El instructor cierra el capítulo aconsejando practicar intensamente con todas las tablas disponibles: mezclar AND, OR, extraer fechas y usar BETWEEN para dominar el filtrado de un solo origen de datos, preparándose así para el siguiente nivel, que será aprender a cruzar e interconectar múltiples tablas.

Filtrar productos con precio mayor a cero:

```sql
SELECT * FROM Productos WHERE prod_precio > 0;
```

Trae productos cuyo precio sea mayor a cero, O cuyo ID de proveedor sea mayor a 10

```sql
SELECT * FROM Productos WHERE prod_precio > 0 OR prob_id > 10;
```

Trae productos con precio mayor a cero Y que pertenezcan a los proveedores del 11 al 49

```sql
SELECT * FROM Productos WHERE prod_precio > 0 AND (prob_id > 10 AND prob_id < 50);
```

Asignarle la letra "p" a la tabla Productos para acortar la escritura y evitar ambigüedades

```sql
SELECT p.prod_description, p.prod_precio, p.prob_id 
FROM Productos p 
WHERE p.prod_precio > 0;
```

Filtrar fechas mayores a un día específico

```sql
SELECT * FROM Ventas b WHERE b.ventas_fecha > '2018-01-02';
```

Filtrar fechas usando "Mayor que" y "Menor que" con AND

```sql
SELECT * FROM Ventas b WHERE b.ventas_fecha > '2018-01-02' AND b.ventas_fecha < '2018-01-04';
```

Trae solo las ventas del año 2018

```sql
SELECT * FROM Ventas b WHERE YEAR(b.ventas_fecha) = 2018;
```

Trae las ventas de los meses posteriores a enero

```sql
SELECT * FROM Ventas b WHERE MONTH(b.ventas_fecha) > 1;
```

Filtrar un rango exacto de fechas, en este caso entre el 1 y el 3 de enero

```sql
SELECT * FROM Ventas b WHERE b.ventas_fecha BETWEEN '2018-01-01' AND '2018-01-03';
```

Buscar el historial de ventas de un producto en específico usando su ID

```sql
SELECT * FROM Ventas_Detalle bd WHERE bd.prod_id = 1128;
```

## 27. Unión de tablas con clausula WHERE

En esta clase, el profesor enseña cómo extraer información que está repartida en diferentes tablas y juntarla en un solo resultado. Aunque menciona que más adelante en el curso enseñará el método "profesional" o estándar de la industria (utilizando las cláusulas JOIN, INNER JOIN, LEFT JOIN), esta lección se centra en un método más rudimentario pero totalmente funcional: Unir tablas directamente usando las cláusulas FROM y WHERE.

**1. El Riesgo de No Filtrar (El Producto Cartesiano)**

¿Qué pasa si solo pongo dos tablas en el FROM sin un WHERE?
Si escribes SELECT * FROM Ventas v, Clientes c; el motor de la base de datos multiplicará cada registro de Ventas por cada registro de Clientes. Si tienes 1,000 ventas y 1,000 clientes, el resultado será de 1,000,000 de filas sin sentido. Esto demora muchísimo y puede colapsar el programa.

La solución: Siempre debes decirle al motor cómo se relacionan esas tablas a través de un campo en común (generalmente un ID).

**2. La Regla de Oro para Unir**

Para que la unión funcione correctamente y actúe como un INNER JOIN (donde solo se muestran los registros que coinciden en ambas tablas), debes establecer la igualdad en el WHERE.

Ejemplo: WHERE v.cliente_id = c.cliente_id
(El ID del cliente en la tabla de Ventas debe ser exactamente el mismo que el ID en la tabla de Clientes).

**3. Escalando la Consulta (Construyendo una Factura Completa)**

El profesor demuestra el poder de SQL uniendo cinco tablas distintas paso a paso para reconstruir el detalle completo de una venta:

    Ventas (b) + Clientes (c):

        - Unión: b.cliente_id = c.cliente_id
        - Obtenemos: Número de factura, fecha, y el nombre del cliente.

    + Ventas_Detalle (bd):

        - Unión: bd.ventas_id = b.ventas_id
        - Obtenemos: Los IDs de los artículos comprados en esa factura. (Aquí las filas se multiplican por la cantidad de productos comprados en una sola factura).

    + Productos (p):

        - Unión: bd.prod_id = p.prod_id
        - Obtenemos: El nombre/descripción del producto, no solo su ID.

    + Proveedores (pr):

        - Unión: p.prov_id = pr.prov_id
        - Obtenemos: El nombre de la empresa proveedora de ese producto específico.

**4. Filtrado Adicional**

Incluso cuando estás usando el WHERE para unir tablas, puedes seguir usándolo para filtrar datos simultáneamente usando AND.

Ejemplo del profesor: AND c.cliente_id > 1 (Para excluir al cliente con ID 1, que era el "Consumidor Final" genérico).

**Reflexión Final del Profesor**

¿Es esto ilegal? No. El profesor aclara que "no hay una policía de SQL". Esta sintaxis es válida y hace el trabajo.

¿Cuál es la limitación? Este método es estricto: solo trae registros si hay coincidencias exactas en todas las tablas unidas. Si quisieras, por ejemplo, "traer todas las ventas, incluso si por error se borró el cliente de la base de datos", este método no te serviría (la venta desaparecería del resultado). Para escenarios más flexibles donde necesitas llenar espacios vacíos con valores nulos (NULL), se utilizan obligatoriamente las sentencias JOIN (como el LEFT JOIN), que se abordarán en capítulos futuros.

```sql
SELECT 
    b.numero_factura, 
    b.cliente_id, 
    c.razon_social, 
    b.fecha, 
    bd.prod_id, 
    p.descripcion, 
    pr.prov_id, 
    pr.nombre  
FROM 
    Ventas b, 
    Clientes c, 
    Ventas_detalle bd, 
    Productos p, 
    Proveedores pr
WHERE 
    b.cliente_id = c.cliente_id      -- 1. Une la tabla Ventas con Clientes
    AND c.cliente_id > 1             -- 2. Filtra para excluir al "Consumidor Final" (ID = 1)
    AND bd.ventas_id = b.ventas_id   -- 3. Une Ventas_Detalle con la tabla Ventas
    AND bd.prod_id = p.prod_id       -- 4. Une Productos con Ventas_Detalle
    AND p.prov_id = pr.prov_id;      -- 5. Une Proveedores con Productos
```

## 28. Clausula ORDER BY

En esta clase, el profesor introduce la cláusula ORDER BY (Ordenar por), que se utiliza para organizar el conjunto de resultados que nos devuelve una consulta. Un punto clave que menciona es que esta instrucción actúa sobre los datos una vez que ya han sido filtrados y procesados por el motor, por lo que no es necesario que las columnas por las que ordenamos tengan índices creados previamente.

**1. Ubicación en la Sintaxis (El Orden Importa)**

Para que el motor de SQL no devuelva un error de sintaxis, el ORDER BY siempre debe colocarse después de la cláusula WHERE.

Estructura lógica: SELECT ➔ FROM ➔ WHERE ➔ ORDER BY.

**2. Tipos de Ordenamiento (Ascendente y Descendente)**

Ascendente (Por defecto): Si solo colocas el nombre del campo, SQL ordenará de menor a mayor (de la A a la Z para textos, o del 0 al 9 en números).

Descendente (DESC): Si quieres que el orden sea de mayor a menor (de la Z a la A, o del más reciente al más antiguo), debes agregar explícitamente la etiqueta DESC justo después del nombre del campo.

**3. Ordenamiento Múltiple**

Puedes ordenar por más de un campo al mismo tiempo separándolos con comas. El motor ordenará por el primer campo y, si encuentra valores repetidos (por ejemplo, ventas hechas el mismo día), utilizará el segundo campo para desempatar.

Ejemplo del profesor: Ordenar primero por la fecha de la venta de forma descendente (las más nuevas primero) y, dentro de una misma fecha, ordenar los productos alfabéticamente (ascendente).

**4. Ordenar Campos de Múltiples Tablas**

Como esta cláusula opera sobre el resultado final que ya armaste en el SELECT, puedes ordenar libremente usando campos que provienen de tablas completamente distintas (por ejemplo, ordenar por una fecha de la tabla Ventas y una descripción de la tabla Productos).

**Consultas SQL utilizadas en la clase**

A continuación, la evolución de las sentencias que el profesor aplicó al final de la consulta gigante de la clase anterior:

Ordenar por descripción de forma alfabética (Ascendente por defecto):

```sql
-- (Aquí iría todo el SELECT, FROM y WHERE de la clase anterior)
ORDER BY p.descripcion;
```

Ordenar por descripción de forma Descendente (De la Z a la A):

```sql
ORDER BY p.descripcion DESC;
```

Ordenamiento múltiple combinado (Fechas y Textos de distintas tablas):
(Ordena por fecha desde la más reciente a la más antigua y, si hay varias ventas el mismo día, las ordena alfabéticamente por producto)

```sql
ORDER BY b.ventas_fecha DESC, p.descripcion; 
-- (Nota: Al no poner nada después de 'descripcion', asume que es ascendente)
```

## 29. Funciones SUM, COUNT, MAX, AVG y MIN

En esta clase, el profesor introduce las Funciones de Agregación. Estas funciones nos permiten realizar cálculos matemáticos y estadísticos rápidos sobre un conjunto de datos (por ejemplo, toda una columna o los resultados filtrados por un WHERE).

El profesor destaca que el motor de base de datos (MySQL) está altamente optimizado para realizar estas operaciones a una velocidad impresionante (en milisegundos), incluso si la tabla tiene miles o millones de registros.

A diferencia de un SELECT normal que te devuelve filas y filas de información, estas funciones analizan esas filas y te devuelven un único valor (como un total, un promedio, etc.).

**1. COUNT (Contar)**

¿Qué hace? Cuenta la cantidad de registros (filas) que devuelve una consulta.

¿Cómo se usa? Generalmente se escribe con un asterisco: COUNT(*). No necesita analizar un campo en específico, solo cuenta cuántas "líneas" existen.

Ejemplo de uso: Saber cuántas ventas se hicieron en un día específico, o cuántos registros totales tiene una tabla entera si no usas un WHERE.

**2. SUM (Sumar)**

¿Qué hace? Suma los valores numéricos de una columna específica.

¿Cómo se usa? A diferencia del COUNT, aquí sí o sí debes indicarle entre los paréntesis qué columna quieres sumar: SUM(total).

Ejemplo de uso: Calcular la facturación total sumando el importe de todas las ventas de enero.

**3. MIN (Mínimo)**

¿Qué hace? Busca y te devuelve el valor numérico más bajo dentro de una columna.

¿Cómo se usa? Se le pasa el nombre de la columna: MIN(total).

Ejemplo de uso: Descubrir cuál fue la factura de menor valor (la venta más pequeña) en un periodo de tiempo.

**4. MAX (Máximo)**

¿Qué hace? Busca y te devuelve el valor numérico más alto dentro de una columna.

¿Cómo se usa? Se le pasa el nombre de la columna: MAX(total).

Ejemplo de uso: Descubrir cuál fue la factura más grande (la mejor venta) del mes.

**5. AVG (Average / Promedio)**

¿Qué hace? Suma todos los valores de una columna y los divide por la cantidad de registros, calculando el promedio matemático.

¿Cómo se usa? Se le pasa el nombre de la columna: AVG(total).

Ejemplo de uso: Saber cuál es el "ticket promedio" (cuánto gasta en promedio un cliente por compra).

**Consultas SQL utilizadas en la clase**

Aquí tienes las sentencias que el profesor ejecutó para demostrar estas funciones, aplicando alias (AS) para que los resultados se vean más prolijos:

Contar cuántas ventas hubo en un día específico:

```sql
SELECT COUNT(*) AS Registros 
FROM Ventas 
WHERE ventas_fecha = '2018-01-02';
```

Contar cuántos registros totales tiene toda la tabla (Sin WHERE):

```sql
SELECT COUNT(*) AS Registros 
FROM Ventas;
```

Sumar la facturación total del mes de enero de 2018:

```sql
SELECT SUM(total) AS Total 
FROM Ventas 
WHERE YEAR(ventas_fecha) = 2018 AND MONTH(ventas_fecha) = 1;
```

Obtener la venta más pequeña (MIN), la más grande (MAX) y el promedio (AVG) de ese mismo mes:
(Nota: En la clase el profesor cambió la palabra clave en el mismo código, aquí te muestro cómo sería cada una).

```sql
-- Venta Mínima:
SELECT MIN(total) AS Venta_minima FROM Ventas WHERE YEAR(ventas_fecha) = 2018 AND MONTH(ventas_fecha) = 1;

-- Venta Máxima:
SELECT MAX(total) AS Venta_maxima FROM Ventas WHERE YEAR(ventas_fecha) = 2018 AND MONTH(ventas_fecha) = 1;

-- Promedio de Ventas:
SELECT AVG(total) AS Promedio FROM Ventas WHERE YEAR(ventas_fecha) = 2018 AND MONTH(ventas_fecha) = 1;
```

## 30. Clausula GROUP BY

En este capítulo, el profesor introduce el "aliado perfecto" de las funciones matemáticas que vimos en la clase anterior: la cláusula GROUP BY (Agrupar por).

Esta instrucción nos permite tomar una gran cantidad de datos, agrupar los que tienen características en común (por ejemplo, agrupar las ventas por mes o por producto) y aplicarle a cada grupo una función de agregación (SUM, COUNT, AVG, etc.) para obtener subtotales.

**El Problema: Usar funciones sin agrupar**

El profesor comienza demostrando el error más común al empezar con SQL.

¿Qué pasa si pido el ID del producto y un COUNT(*) pero NO uso GROUP BY?
El motor se confunde. La función COUNT(*) quiere devolver un solo número (el total de todos los registros), pero al pedirle también el ID del producto, SQL tomará el primer ID que encuentre al azar y lo pondrá al lado de ese número gigante. El resultado es información falsa y sin sentido (ej. "El producto ID 36 se vendió 55,000 veces", cuando en realidad 55,000 es el total de la tabla completa).

**La Solución: Agrupando los datos**

Para solucionar esto, le decimos explícitamente al motor cómo queremos que divida y cuente esos datos usando GROUP BY. El profesor muestra dos ejemplos muy potentes:

**Ejemplo 1: Conteo de Ventas por Producto**

El objetivo era saber exactamente cuántas veces se vendió cada producto individual en la tabla de detalles de venta.

Se pide el ID del producto y se cuenta la cantidad de veces que aparece usando COUNT(*) AS ventas.

Al final de la sentencia, se agrega GROUP BY bd.prod_id.

Resultado: Una lista perfecta donde cada producto aparece una sola vez junto a la cantidad exacta de veces que fue facturado. (Además, el profesor unió esto con la tabla Productos usando un WHERE para poder mostrar el nombre del producto y no solo su ID).

**Ejemplo 2: Suma de Facturación por Año y Mes (Agrupamiento Múltiple)**

El objetivo era armar un reporte de ventas totales agrupado mes a mes.

Funciones en el SELECT: El profesor extrae el año y el mes directamente de la fecha usando funciones integradas y les asigna un alias: YEAR(ventas_fecha) AS año, MONTH(ventas_fecha) AS mes.

La Suma: Calcula el total facturado con SUM(total).

Agrupamiento Múltiple: Utiliza GROUP BY año, mes. Esto le dice a SQL: "Primero haz grupos por año (2018, 2019, etc.) y dentro de cada año, haz subgrupos por cada mes. A cada uno de esos subgrupos, aplícale la suma".

Resultado: Una tabla gerencial perfecta y generada en milisegundos que muestra: Año, Mes y el Total facturado en ese periodo.

**Consultas SQL utilizadas en la clase**

Contar cuántas veces se vendió cada producto (Usando GROUP BY):

```sql
SELECT bd.prod_id, COUNT(*) AS ventas 
FROM Ventas_detalle bd 
GROUP BY bd.prod_id;
```

Agregando el nombre del producto al conteo (Uniendo tablas):

```sql
SELECT bd.prod_id, p.descripcion, COUNT(*) AS ventas 
FROM Ventas_detalle bd, Productos p 
WHERE p.prod_id = bd.prod_id 
GROUP BY bd.prod_id, p.descripcion;
```

(Nota del profesor: En algunos motores de bases de datos, si agregas una columna nueva en el SELECT como p.descripcion, el sistema te exigirá que también la agregues en la lista del GROUP BY separada por coma).

Reporte de ventas sumadas por Año y por Mes:

```sql
SELECT 
    YEAR(b.ventas_fecha) AS año, 
    MONTH(b.ventas_fecha) AS mes, 
    SUM(b.total) AS Total 
FROM Ventas b 
GROUP BY año, mes;
```

**CLASE ADICIONAL PARA ENTENDER EL GROUP BY**

La Analogía de la Zapatería:

Imagina que eres el dueño de una zapatería. Al final del día, tienes una caja llena de 100 recibos de ventas totalmente desordenados.

Si alguien te pregunta: "¿Cuánto dinero hicimos hoy en total?", tú simplemente tomas la calculadora y sumas los 100 recibos de golpe. Eso en SQL es usar una función matemática sola: SELECT SUM(total) FROM Recibos;.

Pero, ¿qué pasa si alguien te pregunta: "¿Cuánto dinero vendimos por cada marca de zapatos?"

Para responder a esa segunda pregunta, tu cerebro hace lo siguiente de forma natural:

    - Sacas todos los recibos de la caja.

    - Empiezas a hacer pilitas o grupos sobre la mesa: haces una pila con los recibos de Nike, otra pila con los de Adidas y otra con los de Puma. (¡Esto exactamente es lo que hace el GROUP BY!)

    - Finalmente, tomas tu calculadora y aplicas la matemática (SUM, COUNT, AVG) a cada pila por separado.

**Ejemplo 1: Contando cosas (COUNT)**

Imagina que tenemos una tabla muy pequeña en una veterinaria llamada Mascotas:


| Nombre | Especie |
|--------|---------|
| Luna   | Perro   |
| Milo   | Gato    |
| Rex    | Perro   |
| Nemo   | Pez     |
| Bella  | Perro   |
| Simba  | Gato    |

Pregunta de negocio: "¿Cuántas mascotas tenemos de cada especie?"

La Consulta SQL:

```sql
SELECT Especie, COUNT(*) AS Cantidad
FROM Mascotas
GROUP BY Especie;
```

¿Qué hace el motor de SQL paso a paso aquí?

    - FROM Mascotas: Va a buscar la tabla.

    - GROUP BY Especie: Crea tres "cajas" invisibles porque detectó tres valores distintos (Perro, Gato, Pez). Mete a Luna, Rex y Bella en la caja de Perros; a Milo y Simba en la de Gatos; y a Nemo en la de Peces.

    - SELECT Especie, COUNT(*): Te muestra el nombre de la caja (Especie) y cuenta cuántos registros quedaron adentro de cada una.

El Resultado visual:


| Especie | Cantidad |
|---------|----------|
| Perro   | 3        |
| Gato    | 2        |
| Pez     | 1        |

**Ejemplo 2: Sumando dinero (SUM)**

Ahora volvamos a la zapatería. Tenemos una tabla llamada Ventas_Zapatos:

| Marca  | Precio |
|--------|--------|
| Nike   | $100   |
| Adidas | $80    |
| Nike   | $120   |
| Puma   | $60    |
| Adidas | $90    |

Pregunta de negocio: "¿Cuánto dinero recaudó cada marca?"

La Consulta SQL:

```sql
SELECT Marca, SUM(Precio) AS Total_Recaudado
FROM Ventas_Zapatos
GROUP BY Marca;
```

¿Qué hace el motor de SQL?: 

Agrupa las filas por "Marca". Luego, en lugar de contar cuántos hay, toma los valores de la columna "Precio" que quedaron en cada grupo y los suma. (En la pila de Nike suma 100 + 120).

El Resultado visual:

| Marca  | Total_Recaudado |
|--------|-----------------|
| Nike   | $220            |
| Adidas | $170            |
| Puma   | $60             |

**⚠️ La Regla de Oro del GROUP BY (Para que nunca te dé error)**

Si entiendes esta regla, nunca más tendrás problemas al programar agrupamientos:

Si en tu SELECT pones una columna que NO tiene una fórmula matemática al lado (como SUM, COUNT, MAX, AVG), esa columna TIENE QUE IR OBLIGATORIAMENTE escrita en tu GROUP BY.

Ejemplo de lo que está MAL (Te dará error):

```sql
SELECT Marca, Color, SUM(Precio)
FROM Ventas_Zapatos
GROUP BY Marca; 
-- ¡ERROR! Pusiste "Color" arriba en el SELECT, pero olvidaste ponerlo abajo en el GROUP BY. SQL no sabe cómo agrupar los colores dentro de las marcas.
```

Ejemplo de lo que está BIEN:

```sql
SELECT Marca, Color, SUM(Precio)
FROM Ventas_Zapatos
GROUP BY Marca, Color; 
-- ¡PERFECTO! Ahora SQL hará grupos más específicos (Ej: Hará una pila para "Nike Rojos", otra para "Nike Azules", etc).
```

| Marca  | Color  | Total_Recaudado |
|--------|--------|-----------------|
| Nike   | Rojo   | $210            |
| Nike   | Azul   | $120            |
| Adidas | Negro  | $170            |
| Adidas | Blanco | $85             |

**¿Por qué es tan potente esto?**

Porque si solo hubieras agrupado por Marca, sabrías que Nike vendió $330 en total. Pero al agrupar por Marca y Color, como dueño del negocio ahora sabes exactamente qué modelo específico es el que te está dejando más dinero (los Nike Rojos).

## 31. Clausula HAVING

En esta clase, el profesor introduce la cláusula HAVING, comúnmente conocida como "el WHERE del GROUP BY". Su propósito exclusivo es permitirnos establecer filtros basados en resultados de funciones de agregación (como SUM, COUNT, MAX, etc.), algo que la cláusula WHERE tradicional no puede hacer.

**El Problema: ¿Por qué no puedo usar WHERE?**

Supongamos que armaste tu reporte agrupado de ventas por mes usando SUM(total) AS total_mes. Ahora, tu jefe te pide: "Solo muéstrame los meses donde el total haya superado el millón de dólares".

Tu instinto lógico sería escribir: WHERE total_mes > 1000000.
Pero esto da error. El motor de base de datos te dirá "No conozco la columna total_mes".

¿Por qué pasa esto? Porque el WHERE trabaja directamente leyendo los datos puros (crudos) de las tablas antes de que la base de datos comience a sumar, contar o agrupar. Como esa columna total_mes se crea "en el aire" durante el agrupamiento, el WHERE es incapaz de verla.

**La Solución: HAVING**

Para solucionar esto, SQL tiene la instrucción HAVING. Esta cláusula hace exactamente lo mismo que el WHERE (filtrar), pero actúa después de que el GROUP BY ha terminado de hacer todas sus "pilitas" matemáticas.

Regla general: Si vas a filtrar usando una columna normal (ej. fechas, nombres), usas WHERE. Si vas a filtrar usando una columna calculada (ej. sumas totales, conteos), usas HAVING.

**El Concepto Clave: Los "Dos Mundos" de SQL**

Para que nunca más te confundas sobre qué cláusula poner primero, el profesor divide una consulta SQL en dos fases lógicas de ejecución:

    1. El Mundo del Motor (Procesamiento inicial):
    Aquí actúan SELECT, FROM y WHERE. La base de datos va a las tablas físicas, trae la información bruta y filtra qué registros sirven y cuáles no.

    2. El Mundo de los Resultados (Post-procesamiento):
    Una vez que el motor ya tiene los datos crudos filtrados sobre la mesa virtual, entran a actuar GROUP BY, HAVING, ORDER BY y LIMIT. Estas instrucciones agrupan, filtran matemáticas y ordenan estéticamente el reporte final.

**Ejemplos Prácticos de la Clase**


Filtrar ventas mensuales superiores a un millón:

Aquí agrupamos por año y mes, y luego filtramos para quedarnos solo con los meses muy exitosos.

```sql
SELECT 
    YEAR(ventas_fecha) AS año, 
    MONTH(ventas_fecha) AS mes, 
    SUM(total) AS Total_Mes
FROM Ventas
GROUP BY año, mes
HAVING Total_Mes > 1000000;
```

Crear un Ranking de Productos más vendidos:

En el capítulo anterior contamos cuántas veces se vendió cada producto. Ahora, usando HAVING y ORDER BY, filtramos para ver solo los que se vendieron más de 100 veces y los ordenamos de mayor a menor para ver a los "campeones" primero.

```sql
SELECT 
    bd.prod_id, 
    COUNT(*) AS veces_vendido 
FROM Ventas_detalle bd
GROUP BY bd.prod_id
HAVING veces_vendido > 100
ORDER BY veces_vendido DESC;
```

(Nota: Fíjate cómo el ORDER BY sí funciona con campos calculados, porque pertenece al "segundo mundo" donde los cálculos ya están hechos).


## 32. Clausula IN / NOT IN

## 33. Clausula LIKE

## 34. Clausula JOIN (Union de tablas)

## 35. Clausula LEFT & RIGHT JOIN