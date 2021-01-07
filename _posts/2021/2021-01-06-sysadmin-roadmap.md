---
layout: post
title: Emprendiendo el camino a SysAdmin
---

# INTRODUCCIÓN

Mi pasión son los servidores y la seguridad informática y para poder asentar y perfeccionar mis conocimientos, al igual que en cualquier carrera en tecnología, debo mantenerme en constante aprendizaje. El problema, soy un poco - por no decir muy - desordenado, así que siempre intento seguir alguna guía para no perderme. Por ello, en esta post quiero compartir un par de recursos que he encontrado relacionados con el camino a seguir, en este caso, enfocado a la parte de SysAdmin.

# ROADMAP: emprendiendo el camino

Lo primero que se me vino a la mente - obviamente - fue _googlear_ algún _roadmap_ relacionado con el rol de sysadmin. Si bien existe un _devops roadmap_ hay cierta polémica en cuanto a la denominación del rol SysAdmin / SRE vs. DevOps (pero eso lo dejo al equipo de [Polémica en /var](https://open.spotify.com/show/4aSX6qCCbNLmOUX4fftc5M?si=V4PHPlWxRhOXqP_g8_-5qg) o a mi mentor [peladonerd](https://www.youtube.com/watch?v=xin3Tb8f31M)). 

En un artículo de [redhat.com](https://www.redhat.com/sysadmin/sysadmin-devops), titulado __From Sysadmin to DevOps__ nos expone la importancia de la evolución del rol de Sysadmin a la par de la evolución de las empresas/organizaciones. Además, también resume las posturas opuestas que históricamente separaban a los equipos de desarrollo y operaciones, exponiendo que un nuevo enfoque como DevOps es el mejor para solucionar esta brecha.

Para que una empresa pueda adoptar un enfoque DevOps, el artículo menciona valores, principios y prácticas que son importantes para lograrlo:

__Valores de DevOps__

- Cultura representada por la comunicación humana, los procesos técnicos y las herramientas.
- Automatización de los procesos.
- Medición de los KPIs (Key Performance Indicators).
- Compartir feedback, mejores prácticas y conocimientos.

__Principios de DevOps__

- Desarrollo y pruebas en un entorno similar al de producción.
- Implementación con procesos repetibles y confiables.
- Monitoreo y validación de la calidad operacional.
- Amplificación de los bucles de feedback.

__Prácticas de DevOps__

- Configuración de autoservicio.
- Aprovisionamiento automatizado.
- Construcción continua.
- Integración continua.
- Entrega continua.
- Gestión de versiones automatizada.
- Pruebas incrementales.

Además, también detalla algunos aspectos clave a tener en cuenta:

- El control de versiones, teniendo en cuenta a Git como principal sistema de control de versiones.
- El enfoque Pets vs. Cattle (mascotas vs. ganado), se pasa de tener infraestructuras inmutables a infraestructuras dinámicas.
- Logs y observabilidad, centralizando los registros de toda la infraestructura para poder observar los eventos en un solo lugar.
- Idempotencia y automatización.
- Seguridad por defecto.

Este artículo [3], así como en [5], hacen referencia a un recurso en [radmap.sh](https://roadmap.sh), que es un Roadmap para DevOps [6].

![DevOps Roadmap](https://roadmap.sh/roadmaps/devops.png)

Este roadmap es un gran recurso del cual guiarse para los que, como yo, necesiten una guía de que pasos seguir en el camino al rol de sysadmin / sre / devops.

Pero también quiero mencionar otro artículo que encontré al pasar, relacionado con un roadmap para aprender nodejs. En [1], nos recomienda en primera instancia definir cuál es nuestro objetivo a la hora de aprender una nueva tecnología - en este caso, nodejs -. Es importante tener en mente el por qué queremos aprender dicha tecnología por sobre otras, que empresas la utilizan y que problemas pudieron resolver con dicha tecnología. En mi caso particular, quiero orientarme al rol de sysadmin / sre / devops, pero también quiero poder terminar mi proyecto de tesis como objetivo principal en este nuevo año 2021. Por lo cual, teniendo como referencia el roadmap de [6], me he inclinado por la elección de node por sobre los otros lenguajes por algunas razones:

- El lenguaje base de node es JS, y tengo pensado desarrollar APIs del lado del servidor y aplicaciones frontend para consumir dichas APIs, para lo cual utilizaré React - también basado en JS.
- Cuento con ciertos conocimientos en JS por algunos trabajos que he efectuado en Angular y React, por lo cual me parece la opción más adecuada.
- La curva de aprendizaje va a ser más rápida, ya que estaría utilizando un único lenguaje tanto del lado del servidor como del lado del cliente.

Si bien me he inclinado por Node en esta ocasión, también tengo pensado aprender Python, ya que me brinda un mayor panorama en otros campos como Machine Learning, en el cual ha ganado mucho terreno.

Tengo mi objetivo claro, tengo decidido por donde empezar, así que es hora de ponerse manos a la obra y comenzar a recorrer el camino.

Para concluir, en las referencias adjuntas hay un par de recursos adicionales. Tanto en [1] como en [2], tenemos a disposición un roadmap para NodeJS. Por otro lado, en [4] IBM nos proporciona un recurso para aprender Linux basado en la certificación LPIC-1 que pueden ser de gran utilidad en nuestro camino de aprendizaje.

Sin más, ¡happy learning!

# Referencias

1. [geeksforweeks.org: Best Way to Learn NodeJS – A Complete Roadmap](https://www.geeksforgeeks.org/best-way-to-learn-nodejs-a-complete-roadmap/?ref=rp)
2. [Aliyr: Nodejs Developer Roadmap](https://github.com/aliyr/Nodejs-Developer-Roadmap)
3. [From sysadmin to DevOps](https://www.redhat.com/sysadmin/sysadmin-devops)
4. [Learn Linux, 101: A roadmap for LPIC-1](https://developer.ibm.com/technologies/linux/tutorials/l-lpic1-map/)
5. [El camino al SRE SENIOR - QUE APRENDER PARA SER SENIOR SYSADMIN!](https://www.youtube.com/watch?v=lYHnv_-H6UY)
6. [DevOps Roadmap](https://roadmap.sh/devops)
