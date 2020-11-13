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

- Una Maquina Virtual (VM) Ubuntu 18.04 desplegada con la herramienta _multipass_. También puede utilizarse otras herramientas de virtualización como docker, virtualbox o vmware.
- Una terminal

#### Instalación de Tmux

Lo primero que haremos es levantar nuestra VM con la herramienta multipass (o su herramienta de virtualización de preferencia) con el comando:

```

multipass launch --name tmux-poc bionic

```

Posteriormente, ingresaremos a nuestra VM creada a través del comando:

```

multipass shell tmux-poc

```

{% include image.html url="2020/november/tmux_002.png" description="Figura 2: Levantando nuestra VM con multipass" %}

Una vez dentro de nuestra VM, procedemos a instalar _tmux_. Para ello, nos apoyamos en la documentación del mismo, que puede encontrarse en su [wiki de github](https://github.com/tmux/tmux/wiki/Installing){:target="_blank"}. En nuestro caso, tenemos un sistema operativo ubuntu, por lo cual ejecturemos los siguientes comandos:

```

# comandos opcionales para actualizar los paquetes del sistema
sudo apt-get update && \
sudo apt-get upgrade

# instalación de tmux
sudo apt-get install tmux

```

{% include image.html url="2020/november/tmux_003.png" description="Figura 3: Instalación de tmux en Ubuntu 18.04" %}

En mi caso, vemos que ya viene instalado tmux por defecto en la versión de ubuntu utilizada (2.6-3ubuntu0.2). Ahora, comenzaremos a utilizar nuestra herramienta. Lo primero que haremos es crear una sesión con el comando:

```

tmux

```

Como pueden ver, es muy sencillo. Una vez iniciada una sesión _tmux_, podemos dividir nuestro terminal en varios _paneles_ para realizar distintas tareas en una única sesión. Para ello, emplearemos los siguientes atajos de teclado:

- Ctrl + b y luego % (para dividir nuestra terminal verticalmente)
- Ctrl + b y luego " (para dividir nuestra terminal horizontalmente)
- Ctrl + b y flecha de direccionamiento (para ir cambiando de panel: arriba, abajo, izquierda, derecha)

Debemos tener eestos atajos, ya que lo utilizaremos constantemente a la hora de navegar entre los paneles que vayamos creando. En nuestro caso, dividiremos nuestra terminal en cuatro paneles, como se aprecia en la imagen:

{% include image.html url="2020/november/tmux_004.png" description="Figura 4: Sesión tmux y división en paneles" %}

Al utilizar el atajo de teclado _Ctrl + b y luego q_, podemos ver la numeración de los paneles en que dividimos nuestro terminal, marcando de un color distinto (en este caso rojo) el panel que se encuentra activo actualmente.

Comenzaremos manteniendo en uno de los paneles un _htop_ corriendo, para chequear el estado de los recursos de nuestra VM.

```

htop

```

{% include image.html url="2020/november/tmux_005.png" description="Figura 5: Uso de la herramienta htop" %}

Luego, nos dirigimos a otro panel para instalar una base de datos, por ejemplo, mongo:

```

sudo apt-get update && \
sudo apt-get install -y mongodb

```

Comenzaremos a utilizar la base de datos insertando algunos registros ficticios a modo de prueba. Para ello, ejecutamos simplemente el siguiente comando para poder ingresar a la CLI de mongo:

```

mongo

```

{% include image.html url="2020/november/tmux_006.png" description="Figura 6: Utilizando la CLI de mongo, previa instalación de la base de datos" %}

Una vez dentro, comenzamos a insertar registros en una colección que llamaremos _clients_:

```

> db.clients.insert({ firstname: 'john', lastname: 'doe', age: 35 })
WriteResult({ "nInserted" : 1 }) 
> db.clients.insert({ firstname: 'mary', lastname: 'jons', age: 24 })
WriteResult({ "nInserted" : 1 }) 
> db.clients.find().pretty() # Para ver los datos ingresados

```

{% include image.html url="2020/november/tmux_007.png" description="Figura 7: Insertando datos en nuesta colección 'clients'" %}

Supongamos que necesitamos mantener la CLI de mongo activa, asi que cambiaremos de panel para realizar otras tareas. Por ejemplo, queremos monitorear los logs de la base de datos. Para ello, podemos utilizar el siguiente comando:

```

tail -f /var/log/mongodb/mongodb.log

```

{% include image.html url="2020/november/tmux_008.png" description="Figura 8: Observando los registros (logs) de mongo" %}

El mismo quedará activo para ir monitoreando que esta pasando en nuestra base de datos. Cambiamos a nuestro último panel y realizaremos algunas acciones en la base de datos, pero esta vez desde fuera. En este caso, importaremos datos en nuestra colección con la herramienta _mongoimport_, utilizando el siguiente comando:

```

mongoimport --db test --collection clients --jsonArray --file data.json

```

Al realizar esta acción, veremos que hubo actividad en el panel donde visualizamos los logs de mongo, y si ejecutamos el comando ```db.clients.find()```, podremos ver que hemos importados nuestros datos con éxito.

{% include image.html url="2020/november/tmux_009.png" description="Figura 9: Importando datos con 'mongoimport'" %}

## Conclusión

Como se puede observar, _tmux_ puede ser muy útil si necesitamos realizar varias tareas a la vez, manteniendo algunas herramientas de monitoreo activas para ir vizualizando en tiempo real que esta pasando en nuestro computador, tener una CLI de base de datos lista para comenzar a ingresar consultas, o realizar tareas de otro tipo mientras estas se mantienen en otros paneles separados.

## Referencias:

- [Tmux Wiki](https://github.com/tmux/tmux/wiki)
- [Mongo import documentation](https://docs.mongodb.com/database-tools/mongoimport/#bin.mongoimport)
