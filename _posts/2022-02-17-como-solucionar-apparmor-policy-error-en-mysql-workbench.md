---
layout: post
title: Cómo solucionar AppArmor policy error en MySQL Workbench Ubuntu
date: 2022-02-07 08:46:07 +0100
---

![Screenshot AppArmor Policy Error](/assets/images/como-solucionar-apparmor-policy-error-en-mysql-workbench-min.png)

El error aparece a intentar gestionar los passwords, cuando se ha instalado
[MySQL Workbench](https://www.mysql.com/products/workbench/)
mediante el Snap Package de Ubuntu.

Esto se debe a que las aplicaciones instaladas mediante Snap están bloqueadas por defecto.

Más info: [Security and sandboxing](https://ubuntu.com/core/docs/security-and-sandboxing).

Por lo tanto, al elegir la opción de `Store in keychain`, MySQL Workbench es bloqueado por el AppArmor.

**Solución**

Para permitir que la aplicación tenga permisos puedes utilizar los siguiente commandos:

```
snap connect mysql-workbench-community:password-manager-service
snap connect mysql-workbench-community:ssh-keys
```
