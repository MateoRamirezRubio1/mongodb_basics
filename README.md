# Manual de Uso de MongoDB

![image](https://github.com/user-attachments/assets/244693a6-be49-4eb7-af88-7ba52ef5bf5e)


Este repositorio está diseñado como una guía de referencia rápida para aprender los comandos básicos al iniciarse en MongoDB. Aquí encontrarás ejemplos de cómo realizar operaciones comunes, tales como crear bases de datos y colecciones, insertar y consultar documentos, así como filtrar y actualizar datos. Este manual es ideal para principiantes que buscan familiarizarse con MongoDB y sus funcionalidades básicas.

</br>

## Tabla de Contenidos

- [Ver bases de datos creadas](#ver-bases-de-datos-creadas)
- [Crear una base de datos en MongoDB](#crear-una-base-de-datos-en-mongodb)
- [Crear una colección e insertar documentos en ella](#crear-una-colección-e-insertar-documentos-en-ella)
- [Ver colecciones creadas](#ver-colecciones-creadas)
- [Ver documentos de una colección](#ver-documentos-de-una-colección)
- [Ver un solo documento de una colección](#ver-un-solo-documento-de-una-colección)
- [Filtrar búsquedas](#filtrar-búsquedas)
- [Profundización en filtrado de búsquedas](#profundización-en-filtrado-de-búsquedas)
- [Operadores de comparación](#operadores-de-comparación)
- [Expresiones regulares](#expresiones-regulares)
- [Contar elementos o documentos](#contar-elementos-o-documentos)
- [Buscar campos en un documento o documentos anidados](#buscar-campos-en-un-documento-o-documentos-anidados)
- [Operadores Lógicos](#operadores-lógicos)
- [Actualizar datos en documentos](#actualizar-datos-en-documentos)
- [Contar cantidad de documentos según el criterio dado](#contar-cantidad-de-documentos-según-el-criterio-dado)
- [Eliminar documentos de una colección](#eliminar-documentos-de-una-colección)

---

</br>

## `Comandos básicos MongoDB`

</br>


<!-- ----------------- -->

### Ver bases de datos creadas
<br>

Se utiliza el comando `show`, así:
</br>

```
show dbs
```

</br>

---
<br>

<!-- ----------------- -->

### Crear una base de datos en Mongodb
<br>

Se utiliza el comando `use`, así:
<br>

```
use <nombreBasedeDatos>
```

*Tener en cuenta: para que la base de datos creada quede en el sistema se debe agregar como mínimo un elemento a una colección en esta.*

<br>

---
<br>

<!-- ----------------- -->

### Crear una colección e insertar documentos en ella
<br>

Para crear una colección solo basta con agregar como mínimo un documento a esta con el comando `insert`, así:
<br>

```
db.<nombreColeccion>.insert({<elemento>: <valor>}, {<elemento>: <valor>})
```

<br>

---
<br>

<!-- ----------------- -->

### Ver colecciones creadas
<br>

Se utiliza el comando `show`, así:
<br>

```
show collections
```

<br>

---
<br>

<!-- ----------------- -->

### Ver documentos de una colección
<br>

Se utiliza el comando `find`, así:
<br>

```
db.<nombreColeccion>.find()
```

<br>

---
<br>

<!-- ----------------- -->

### Ver un solo documento de una colección
<br>

Se utiliza el comando `findOne`, así:
<br>

```
db.<nombreColeccion>.findOne()
```

<br>

---
<br>

<!-- ----------------- -->

### Filtrar búsquedas
<br>

Se utiliza el comando `find`, declarando dentro de este los campos por los que quiere filtrar los documentos, así:
<br>

```
db.<nombreColeccion>.find({<elemento>: <valor>})
```

<br>

---
<br>

<!-- ----------------- -->

### Profundización en filtrado de búsquedas
<br>

La función comando `find` acepta otro parámetro opcional con el que podemos especificar que elementos de los documentos queremos que se muestren o cuales no:
- `1` : Mostrar solo ese elemento en la busqueda.
- `0` : No mostrar ese elemento en la busqueda.

<br>

```
db.<nombreColeccion>.find({<elemento>: <valor>}, {<elemento>: 1})
```

<br>

---
<br>

<!-- ----------------- -->

### Operadores de comparación
<br>

Existen varios operadores de comparación para mejorar las busquedas, estos son:
- `$eq`  =  Igual qué.
- `$ne` != No igual qué.
- `$gt` > Mayor qué.
- `$lt` < Menor qué.
- `$gte` >= Mayor o igual qué.
- `$lte` <= Menor o igual qué.

<br>

```
db.<nombreColeccion>.find({<elemento>: {<operador>: <valor>}})
```

<br>

---
<br>

<!-- ----------------- -->

### Expresiones regulares
<br>

Para una mejor busqueda se pueden utilizar diferentes [expresiones regulares](https://www.mongodb.com/docs/manual/reference/operator/query/regex/ "Documentación"), ejemplo formato del comando:
<br>

```
db.<nombreColeccion>.find({<elemento>: <exprecionRegular>})
```

<br>

---
<br>

<!-- ----------------- -->

### Contar elementos o documentos
<br>

Se utiliza el comando `count` para contar todo tipo de cosas, por ejemplo elementos en una busqueda o documentos en una coleccion, así:
<br>

```
db.<nombreColeccion>.count()
```

<br>

---
<br>

<!-- ----------------- -->

### Buscar campos en un documento o documentos anidados
<br>

Se utiliza `$elemMatch` para una mejor busqueda en un documento o documentos anidados arrojandonos el resultado segun todos nuestros criterios, así:
<br>

```
db.<nombreColeccion>.find({<elemento>: {"$elemMatch": {<criterio1>, <criterio2>}}})
```

<br>

---
<br>

<!-- ----------------- -->

### Operadores Lógicos
<br>

Para mejores busquedas existen los operadores lógicos:
- `$and` : Documentos donde se cumplan todos los criterios de búsqueda. *Este es el operador default de las busquedas en MongoDB.*
- `$or` : Documentos donde se cumpla almenos un criterio de búsqueda.
-  `$nor` : Documentos donde no se cumplan los criterio de busqueda.
- `$not` : Documentos donde no se cumpla el criterio de busqueda.

<br>

```
db.<nombreColeccion>.find({<operador>: [{<criterio1>}, {<criterio2>}]})

db.<nombreColeccion>.find("$not": {<criterio>})
```

<br>

---
<br>

<!-- ----------------- -->

### Actualizar datos en documentos
<br>

Se utiliza la función `update` para actualizar los documentos que sean necesarios, resiviendo este dos parametros, el primero en el que damos el criterio de de los documentos a actualizar y el segundo en el que damos la operación a realizar para actualizar dichos documentos, así:
<br>

```
db.<nombreColeccion>.update({<criterio>}, {<operación>})
```

<br>

---
<br>

<!-- ----------------- -->

### Contar cantidad de documentos según el criterio dado
<br>

Se utiliza la función `count`, así:
<br>

```
db.<nombreColeccion>.count({<criterio1>})
```

<br>

---
<br>

<!-- ----------------- -->

### Eliminar documentos de una colección
<br>

Se utiliza la función `remove` para eliminar los documentos de una colección según los criterios dados, así:
<br>

```
db.<nombreColeccion>.remove({<criterio>})
```

<br>

---
<br>
