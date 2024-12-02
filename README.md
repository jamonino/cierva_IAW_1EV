<br />
<div align="center">
  
  <h1 align="center">1º Evaluación Implantación Aplicaciones Web</h3>

  <p align="left">
    La valoración total del examen es de <b>10 puntos</b>.
    <br />
    <br />
    Lenguajes: SQL, PHP, Javascript, HTML
    ·
    Motor BBDD: MySQL
  </p>
</div>

* Limpieza y estructura de código **1P**
* Presentación interfaz web (tanto Wordpress como páginas independientes) **1P**
  
### PREÁMBULO
Se desea mejorar una tienda de ropa creando una base de datos para gestionar el inventario de productos que tienen. Necesitamos registrar el nombre, precio, inventario y género de cada producto. Además nos piden crear una web corporativa donde se publiquen las novedades de productos.

### Ejercicio 1 (PREPARACIÓN DE ENTORNO DE TRABAJO): **1P**
1. Instala MySQL y crea una base de datos llamada "clothes" con la tabla "products" donde podamos ejecutar los siguientes comandos para insertar registros:
NOTA: Si ya tienes instalado MySQL de otros ejercicios, aprovéchalo ;)
```sql
INSERT INTO products (name, price, stock, gender) VALUES ('pantalones', 2000, 6, 2);
INSERT INTO products (name, price, stock, gender) VALUES ('camiseta', 2200, 4, 2);
INSERT INTO products (name, price, stock, gender) VALUES ('chaqueta', 1000, 1, 2);
INSERT INTO products (name, price, stock, gender) VALUES ('camisa', 3300, 7, 2);
INSERT INTO products (name, price, stock, gender) VALUES ('calcetines', 500, 0, 2);
INSERT INTO products (name, price, stock, gender) VALUES ('blusa', 1800, 1, 1);
INSERT INTO products (name, price, stock, gender) VALUES ('vestido', 4500, 4, 1);
INSERT INTO products (name, price, stock, gender) VALUES ('falda', 3000, 2, 1);
INSERT INTO products (name, price, stock, gender) VALUES ('medias', 1000, 0, 1);
INSERT INTO products (name, price, stock, gender) VALUES ('zapatos de tacón', 3400, 3, 1);
```
2. Despliega Wordpress en un VirtualHost (VH1) con dominio específico (ej. wordpress.cierva) 
NOTA: si ya lo tienes de ejercicios anteriores, aprovéchalo ;)
3. Monta otro virtualhost con dominio especifico (VH2) diferente al anterior (ej. desarrollo.cierva) con capacidad para ejecutar PHP. 

* Fin Ejercicio 1
```
Entregables:
  1. Archivo DB.SQL con los comandos SQL usados para la creación de la BBDD.
  2. Enseñar al profesor VH1 (con WordPress) y VH2 (Con cualquier html) funcionando.
```
NOTA: Si alguien no sabe cómo crear el archivo DB.sql podrá pedirlo al profesor por <a href="mailto:joseantonio.monino@murciaeduca.es">email</a> perdiendo el punto correspondiente con el fin de poder continuar con el resto del examen.

### Ejercicio 2 (PHP): **3P**
Desarrolla una API REST json en la que se pueda administrar la BBDD creada en el ejercicio anterior. Deberá tener los siguientes métodos: GET para obtener un listado de productos, POST para crear un nuevo producto, PUT para editar un producto existente, DELETE para borrar un producto existente. Despliégala en VH2.

A continuación se muestran ejemplos de qué debería devolver esta API para cada método:

* GET - Lista   **1P**
--> REQUEST 
```js
{
}
```
<-- RESPONSE
```js
{
  "responseCode":1,
  "products":[
    {
      "id":1,
      "name":"corbata",
      "price":2900,
      "stock":8,
      "gender":2
    },
    {
      "id":2,
      "name":"bufanda",
      "price":1200,
      "stock":4,
      "gender":1
    }
  ]
}
```

* POST - Crear   **0.5P**
--> REQUEST 
```js
{
  "product":
    {
      "name":"corbata",
      "price":2900,
      "stock":8,
      "gender":2
    }
}
```
<-- RESPONSE
```js
{
  "responseCode":1,
  "product":{
      "id":3,
      "name":"corbata",
      "price":2900,
      "stock":8,
      "gender":2
    }
}
```

* PUT - Editar   **1P**
--> REQUEST 
```js
{
  "product":
    {
      "id":3,
      "name":"corbata roja",
      "stock":45
    }
}
```
<-- RESPONSE
```js
{
  "responseCode":1,
  "product":{
      "id":3,
      "name":"corbata roja",
      "price":2900,
      "stock":45,
      "gender":2
    }
}
```

* DELETE - Borrar   **0.5P**
--> REQUEST 
```js
{
  "product":
    {
      "id":3
    }
}
```
<-- RESPONSE
```js
{
  "responseCode":1
}
```
## EXCEPCIONES

En todos los web services, en caso de excepción se debe devolver un objeto Response con responseCode = 0.
* Fin Ejercicio 2
```
Entregables:
  1. Archivo controller.php que gestione todas las peticiones y genere las respuestas.
  2. Clase product.php que coincida con el modelo de la BBDD.
  3. Clase response.php que tenga los elementos product, products y responseCode y que se usará para respuestas
  4. Cualquier otro archivo necesario para la ejecución del código (configuración de BD, otras clases auxiliares...).
  5. Mostrar al profesor la API funcionando haciendo las llamadas mediante curl, postman o cualquier otra alternativa. 
NOTA: Este ejercicio no tiene interfaz gráfica.
```

### Ejercicio 3 (HTML/Javascript): **2P**
Desarrolla la interfaz gráfica necesaria para que haciendo uso de la API anterior, muestre un listado de productos. En este listado se debe de poder interactuar con cada elemento de modo que podamos tanto editarlo (en cualquiera de sus campos) como eliminarlo.
Además se debe de poder crear un producto nuevo rellenando los campos necesarios. Publica esta vista en VH2.
* Fin Ejercicio 3
```
Entregables:
  1. Archivo principal en html y javascript con el código necesario.
  2. Cualquier otro archivo necesario para la ejecución del código (archivos css, js...).
  3. Mostrar al profesor este ejercicio funcionando.
```

### Ejercicio 4 (API WordPress): **2P**
Modifica el ejercicio anterior y la API desarrollada en el ejercicio 2 para que al crear un elemento nuevo, se pueda marcar como "novedad" con el fin de que al recibirlo el controlador del ejercicio 2, además de crearlo lo publique en el blog de worpress deslegado en VH1.
* Fin Ejercicio 4
```
Entregables:
  1. Todos los archivos modificados o el proyecto completo de VH2.
  2. Mostrar al profesor este ejercicio funcionando.
```

<br />
<div align="center">
  <h1 align="center">¡Mucho ánimo!</h3>
</div>




