---
layout: post
title: Cómo modificar id (PK) con foreign key en MySQL
date: 2022-06-18 08:46:07 +0100
---


Dejo aquí los pasos a seguir para modificar el id (PK) con foreign key en MySQL:

- Eliminar todas las FOREIGN KEYs con otras tablas. Ojo, apuntar como eran para luego recuperarlas.
- Modificar el tipo de dato en la tabla principal. En el ejemplo pasamos a TINYINT UNSIGNED.
- Modificar el tipo de datos en el resto de tablas donde hemos borrado la FOREIGN KEY.
- Recrear las FOREIGN KEYs que hemos borrado en el primer paso. 

**Ejemplo**

```
ALTER TABLE table_2 DROP FOREIGN KEY fk_xxx_xxx;
ALTER TABLE table_1 MODIFY COLUMN id TINYINT UNSIGNED NOT NULL AUTO_INCREMENT;
ALTER TABLE table_2 MODIFY COLUMN table_1_id TINYINT UNSIGNED;
ALTER TABLE table_2 
    ADD CONSTRAINT fk_xxx_xxx
        FOREIGN KEY (table_1_id) REFERENCES table_1 (id)
            ON UPDATE CASCADE ON DELETE SET NULL;
```
