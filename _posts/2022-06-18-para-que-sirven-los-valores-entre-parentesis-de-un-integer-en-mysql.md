---
layout: post
title: Para qué sirven los valores entre paréntesis de un INTEGER en MySQL
date: 2022-06-18 08:45:07 +0100
---

Realizando algunas tareas de migración de datos en MySQL he visto que algunas columnas
con **INT(1)** contenían valores de más de un dígito.

Investigando un poco he encontrado que el número de dentro del paréntesis indica el
ancho máximo que retorna el visualizador. 
Es decir, si tenemos INT(3) y almacenamos "12", el visualizador nos muestra "012".

Aunque es algo que no todos los clientes de MySQL lo interpretan. 

Más info: [MySQL - Numeric Type Attributes](https://dev.mysql.com/doc/refman/8.0/en/numeric-type-attributes.html)

Conclusión: No hace falta poner nada en los paréntesis.

Pero si es importante tener en cuenta el tipo (INTEGER, INT, SMALLINT, TINYINT, MEDIUMINT, BIGINT)
Más info: [MySQL - Integer Types](https://dev.mysql.com/doc/refman/8.0/en/integer-types.html)
