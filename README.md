# BSZInbox-Magic

Es una herramienta para generar correos desechables o teporales , creado por javascrip , html y css donde arquiri una api gratuita mente ..
link de la api utilisada : https://www.1secmail.com/api/ 
en resumen con esta api podras utilizar para generar correos validos con un extencion de envio a una base de datos gratuita con el uso elimitado de correo 

## Ahora la pregunta qui para que te puede servir un correo temporal ?
Registro en Sitios Web: Puedes utilizar un correo temporal al registrarte en sitios web o servicios en línea. Esto es útil para evitar el correo no deseado o newsletters no deseadas que pueden llegar a tu correo principal.

Pruebas y Verificaciones: Al realizar pruebas o verificar cuentas en línea, puedes utilizar un correo temporal para recibir códigos de confirmación o enlaces de verificación. Esto es común al registrarse en plataformas, aplicaciones o foros.

Protección de Privacidad: Si deseas mantener tu privacidad en línea, puedes usar correos temporales para evitar compartir tu dirección de correo principal. Esto ayuda a reducir la cantidad de información personal que compartes en línea.

Evitar el Spam: Al utilizar un correo temporal en situaciones en las que puedes recibir correos no deseados, puedes evitar que tu buzón principal se llene de spam.

Pruebas de Desarrollo: Desarrolladores web y testers pueden utilizar correos temporales para probar la funcionalidad de sistemas de registro y notificaciones por correo electrónico sin utilizar direcciones de correo reales.

Evitar Registro Permanente: En algunos casos, cuando solo necesitas acceder a un servicio o contenido de forma temporal, puedes usar un correo desechable sin comprometer tu dirección de correo principal.

Concurso o Promociones: Al participar en concursos en línea o promociones temporales, puedes usar un correo temporal para recibir información relacionada sin afectar tu bandeja de entrada principal.

Es importante tener en cuenta que, aunque los correos temporales son útiles para ciertos escenarios, no son ideales para situaciones en las que necesitas una comunicación

## Resumen de todo lo que se ocupo en javascript :
Variables:
generateButton: Representa el botón que genera un nuevo correo desechable.
viewMessagesLink: Representa el enlace que redirige al buzón de mensajes del correo desechable.
generatedEmailElement: Representa el elemento de texto que muestra el correo desechable generado.
messagesContainer: Representa el contenedor que muestra el enlace al buzón.
messagesListElement: Representa la lista que mostrará los mensajes.
Variables de Estado:
currentEmail: Almacena el correo desechable actualmente generado.
messageCount: Almacena el número de mensajes.
Funciones:
updateNotificationBadge(): Actualiza el contador de notificaciones (badge) en función de messageCount. Muestra o oculta el badge según sea necesario.
Event Listeners:
generateButton: Genera un nuevo correo desechable al hacer clic en el botón. Actualiza la interfaz y llama a updateNotificationBadge().

viewMessagesLink: Redirige al buzón de mensajes del correo desechable al hacer clic en el enlace. Además, muestra el enlace generado en messagesContainer.

## Observaciones:
Se utiliza la API de 1secmail.com para generar correos desechables y obtener mensajes.
Se manejan errores y se muestran alertas en caso de problemas.
El código HTML tiene elementos con identificadores correspondientes a las variables mencionadas.
![image](https://github.com/AvastrOficial/BSZInbox-Magic/assets/91764815/4d806355-f729-44b4-b9cc-6788c0fa9739)

## Elementos HTML Necesarios:
Se deben tener elementos HTML con los siguientes identificadores:
generateEmail: Botón para generar un nuevo correo desechable.
viewMessages: Enlace para ver mensajes y redirigir al buzón.
email: Elemento span para mostrar el correo desechable generado.
notificationBadge: Elemento span para mostrar el contador de notificaciones.
messagesList: Lista para mostrar mensajes.
randomImage: Elemento de imagen para mostrar imágenes aleatorias.
Este código utiliza JavaScript para interactuar con la API de correos desechables y mostrar imágenes aleatorias al cargar la página

![image](https://github.com/AvastrOficial/BSZInbox-Magic/assets/91764815/ed335459-617c-4899-807b-71e1d06b16b1)

link del la pagina funcionado correctamente vercion 
BSZInbox Magic 0.0.2
https://archivador.foroactivo.com/h3-bszinbox-magic
