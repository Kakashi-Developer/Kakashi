# Política de Privacidad

> Última actualización: 31 de Julio del 2026

La privacidad de los usuarios la tomamos como algo importante al momento de usar a **Kakashi**. No vendemos tus datos, no los utilizamos para publicidad y tampoco buscamos guardar conversaciones completas de los servidores.

Kakashi únicamente procesa y guarda los datos que necesita para que sus comandos, configuraciones, recordatorios, sistemas de moderación y el módulo RPG puedan funcionar correctamente.

## ¿Qué datos recolectamos?

Cuando utilizas a **Kakashi**, el bot puede recibir información básica proporcionada por Discord, como:

* ID del usuario
* ID del servidor
* ID del canal
* ID del mensaje
* Nombre de usuario, avatar y roles cuando algún comando lo necesite
* Comandos utilizados y los argumentos que envías al bot

El nombre, avatar y otros datos visibles de tu perfil normalmente se utilizan en el momento para mostrar embeds, perfiles, rankings o respuestas. No se crea una copia permanente de todo tu perfil de Discord en nuestra base de datos.

## Datos guardados en el módulo RPG

Al registrarte y aceptar las reglas del RPG de **Naruto**, guardaremos los siguientes datos:

* ID del usuario
* Fecha de registro
* Progreso de capítulos y misiones
* Experiencia, nivel y puntos de habilidad
* Ryōs guardados en la billetera y banco
* Vida, energía y chakra
* Control, regeneración y naturalezas de chakra
* Jutsus aprendidos
* Habilidades de combate
* Ninkens o mascotas obtenidas y su progreso
* Objetos, huevos, armas y efectos activos
* Progreso de entrenamientos, exploraciones, cacerías y batallas
* Recompensas y progreso de misiones diarias
* Cooldowns de comandos

Estos datos son necesarios para que no pierdas tu progreso cuando el bot se reinicia o entra nuevamente al servidor.

## Configuración de los servidores

Cuando un administrador configura a Kakashi dentro de un servidor podemos guardar:

* ID del servidor
* Idioma y prefijo configurado
* IDs de canales y roles
* Comandos desactivados en ciertos canales
* Configuración de bienvenidas y despedidas
* Mensajes personalizados y enlaces de imágenes
* Configuración de confesiones
* Configuración de autoroles
* Configuración del mensaje de baneos
* Canal y configuración de eventos aleatorios del RPG
* Advertencias realizadas por los moderadores

En las advertencias se guarda el ID del usuario advertido, ID del moderador, razón de la advertencia y la fecha en la que fue realizada.

En caso de habilitar las notificaciones de Reddit, también se puede guardar el subreddit, canal configurado, texto personalizado y los datos del webhook creado para enviar las publicaciones.

## ¿Cómo utilizamos el contenido de los mensajes?

Kakashi necesita acceder al contenido de algunos mensajes para identificar los comandos utilizados con el prefijo del bot, por ejemplo `k!help`, las menciones directas hacia Kakashi y otras funciones que dependen de mensajes normales.

Si un mensaje no empieza con el prefijo, no menciona al bot y no pertenece a una función habilitada que necesite actividad, normalmente es ignorado y no se guarda en nuestra base de datos.

Para los eventos aleatorios del RPG, los administradores pueden configurar un canal específico. En ese canal el bot revisa la actividad para decidir cuando debe aparecer un evento.

En este sistema:

* No guardamos el texto completo de los mensajes en MongoDB
* Se ignoran mensajes enviados por bots, webhooks y comandos
* Se utiliza temporalmente el ID del usuario y servidor para evitar spam
* Se crea un hash temporal del mensaje para detectar mensajes repetidos
* El hash no permite mostrar nuevamente el mensaje original
* Los hashes y bloqueos se eliminan automáticamente después de un corto periodo
* El contador de actividad también es temporal

El contenido sí puede guardarse cuando el usuario utiliza una función que lo necesita, como recordatorios, configuraciones personalizadas, razones de advertencias o reportes de errores.

## Recordatorios

Cuando utilizas el comando de recordatorios se guarda:

* ID del usuario
* ID del servidor, canal y mensaje
* Texto del recordatorio
* Fecha de creación
* Fecha en la que debe ser enviado
* Si debe enviarse en el canal o por mensaje privado

Después de que el recordatorio es enviado, se elimina de nuestra base de datos. También podrá ser eliminado si el canal, mensaje o usuario ya no puede ser encontrado.

## Confesiones y reportes

Cuando utilizas el sistema de confesiones, Kakashi procesa el texto para enviarlo al canal configurado. El contenido no se guarda en nuestra base de datos, aunque el mensaje publicado seguirá existiendo dentro de Discord hasta que sea eliminado.

En las confesiones anónimas no mostramos públicamente el nombre del usuario, pero el bot necesita conocer temporalmente quién ejecutó el comando para poder procesarlo.

Cuando utilizas `bugreport`, el texto del reporte, tu ID, nombre de usuario y la fecha se envían a un canal privado utilizado por los desarrolladores para revisar errores y abusos.

## Registros técnicos y errores

Cuando ocurre un error, Kakashi puede enviar a los desarrolladores información como:

* Nombre del comando
* Argumentos utilizados
* ID del servidor
* Mensaje técnico del error
* Rastreo interno del error

Estos datos se utilizan únicamente para encontrar problemas y mejorar el funcionamiento del bot.

En producción también podemos utilizar servicios de monitoreo como Sentry para recibir información técnica de fallos, rendimiento y errores del bot.

## Servicios externos

No vendemos ni entregamos tus datos a anunciantes o empresas de publicidad.

Algunas funciones necesitan comunicarse con otros servicios para funcionar. Dependiendo del comando utilizado se puede enviar solamente la información necesaria a:

* Discord, para recibir y enviar mensajes, interacciones y webhooks
* Nuestros proveedores de alojamiento, base de datos y Redis
* Sentry, para monitoreo de errores técnicos
* APIs externas utilizadas por los comandos `chat` y `8ball`
* Un servicio externo de imágenes usado por el comando `ship`, al cual se envían las URLs de los avatares seleccionados
* Reddit, cuando un servidor configura publicaciones automáticas
* Spotify, Lavalink y otros servicios relacionados con búsquedas de música
* Top.gg y otras listas de bots, donde se envían estadísticas generales como cantidad de servidores y shards

Cuando utilizas `chat` o `8ball`, el texto escrito en el comando se envía a una API externa para generar la respuesta. No deberías colocar información privada o sensible dentro de esos comandos.

Las APIs de imágenes de animales o reacciones solamente son utilizadas para obtener una imagen y normalmente no reciben información personal del usuario.

Kakashi no utiliza el contenido de los mensajes para crear, entrenar o mejorar un modelo de inteligencia artificial propio.

## ¿Por cuánto tiempo guardamos los datos?

Los datos del RPG se guardan mientras tu cuenta permanezca registrada o hasta que solicites su eliminación.

Las configuraciones, advertencias y demás datos del servidor se guardan mientras sean necesarios para mantener las funciones configuradas. Actualmente, sacar al bot de un servidor no elimina automáticamente todos los datos guardados de ese servidor, pero el dueño o un administrador puede solicitar su eliminación.

Los recordatorios son eliminados después de ser enviados.

Los contadores, bloqueos, hashes de mensajes y demás datos temporales de Redis son eliminados automáticamente, reemplazados o limpiados cuando dejan de ser necesarios.

Los reportes y registros de errores pueden mantenerse durante el tiempo necesario para investigar y solucionar el problema correspondiente.

Los mensajes enviados dentro de Discord, como confesiones, respuestas del bot o eventos RPG, están almacenados por Discord y pueden permanecer visibles hasta que sean eliminados dentro de la plataforma.

## ¿Cómo puedo solicitar que mis datos sean removidos?

Si deseas eliminar tu cuenta del RPG o cualquier información relacionada con tu ID de usuario, puedes solicitarlo directamente a los desarrolladores en nuestro [servidor de soporte](https://discord.com/invite/kvnGMFg).

El dueño o un administrador de un servidor también puede solicitar que eliminemos la configuración y los datos relacionados con su servidor.

Para evitar que alguien elimine los datos de otra persona o servidor, podemos pedir una comprobación de que la cuenta o servidor realmente te pertenece.

Cuando los datos sean eliminados no podremos recuperar el progreso, objetos, ryōs, jutsus, ninkens ni otra información que pertenecía a la cuenta.

## Cambios en esta política

Esta política puede actualizarse cuando Kakashi agregue, elimine o modifique alguna función que cambie la manera en que utilizamos los datos.

La fecha que se encuentra al principio indicará la última actualización realizada.
