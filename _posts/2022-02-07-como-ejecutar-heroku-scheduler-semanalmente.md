---
layout: post
title: Cómo ejecutar Heroku Scheduler semanalmente
date: 2022-02-07 08:46:07 +0100
---

Este post explica como configurar [Heroku Scheduler](https://elements.heroku.com/addons/scheduler) 
para ejecutar tareas programadas semanalmente.

Por defecto, Heroku Scheduler solo permite lanzar tareas cada 10 minutos, cada hora o diariamente.

Los pasos a seguir serían. Abrir el addon desde consola:
`heroku addons:open scheduler`
o desde el navegador:
`https://dashboard.heroku.com/apps/YOUR_APP_NAME/scheduler?job=new`

Seleccionar la opción de ejecutar diariamente: "Every day at..." y en el commando una de las 
siguiente opciones:

```
if [ "$(date +%u)" = 1 ]; then YOUR_COMMAND; fi # Lunes
if [ "$(date +%u)" = 2 ]; then YOUR_COMMAND; fi # Martes
if [ "$(date +%u)" = 3 ]; then YOUR_COMMAND; fi # Miercoles
if [ "$(date +%u)" = 4 ]; then YOUR_COMMAND; fi # Jueves
if [ "$(date +%u)" = 5 ]; then YOUR_COMMAND; fi # Viernes
if [ "$(date +%u)" = 6 ]; then YOUR_COMMAND; fi # Sabado
if [ "$(date +%u)" = 7 ]; then YOUR_COMMAND; fi # Domingo
```

⚠️**Nota:** Recuerda cambiar *YOUR_COMMAND* por el commando deseado!

Básicamente lo se está haciendo es añadir una clausula de guarda que impide la ejecución del 
commando deseado a no ser que estamos en el día indicado.