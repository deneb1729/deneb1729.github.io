---
layout: post
title: Jugando con Tmux
---

## Introducción

A la hora de administrar sesiones a través de una CLI o interfaz de línea de comandos, a veces necesitamos utilizar más de una terminal. Veamos el siguiente ejemplo:

> Necesitamos conectarnos a un servidor a través de __SSH__, para desplegar una base de datos, por ejemplo __mongodb__, que debe estar escuchando en un determinado puerto las posibles peticiones de conexión al mismo y, al mismo tiempo, ver que esta pasando en el proceso. Además, luego necesita realizar otras tareas como monitorear los recursos del sistema con, por ejemplo, __htop__. Por último, necesita seguir realizando otras tareas comunes como copiar archivos, crear directorios, etc, todo en el mismo servidor en el cual, por motivos de seguridad, un usuario no puede tener más de una sessión _ssh_.

Como podemos observar en esta situación hipotética, necesitamos otra alternativa para poder tener multiples terminales en el mismo servidor. En este caso utilizaremos una herramienta denominada __tmux__.

## Tmux

Tmux es un multiplexor de terminales que nos permite tener varios _pseudo terminales_ en una sola sesión. Esto nos permitirá realizar varias tareas a la vez en una misma sesión. Tmux también nos asegura una persistencia de las sesiones ante una desconexión accidental o la desconexión intencional del usuario.

{% include image.html url="2020/november/tmux_001.png" description="Figura 1: Ejemplo de sesión con tmux" %}

## PoC

Para esta __prueba de concepto__ (__PoC__, por sus siglas en inglés), utilizaremos:

- Maquina Virtual Ubuntu 18.04 desplegada con la herramienta _multipass_
- Una terminal





## Conclusión