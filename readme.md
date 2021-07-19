# Loggers y GZIP



### Incorporar al proyecto de servidor de trabajo la compresión gzip.<br /><br />

**Verificar sobre la ruta /info con y sin compresión, la diferencia de cantidad de bytes devueltos en un caso y otro.**<br />

Cree 2 rutas, ```/info``` sin compresión y ```/infozip``` comprimida.<br /><br />
http://localhost:8080/info<br />
Esta URL, sin compresión pesa **17.5kb**.<br /><br />
http://localhost:8080/infozip<br />
La URL comprimida devuelve un peso de **4.6kb.**
<br />
<br />
<hr />
<br />

### Utilizar como registro de la aplicación de backend eligiendo el logger que más les guste:<br />log4js, winston o pino.
<br />

**Elegir un módulo del servidor para reemplazar los console.log por las funciones de logger, seleccionando el detalle de log entre 3 niveles: info, warning y error utilizando el siguiente criterio:**
- **Loggear todos los niveles a consola (info, warning y error)**
- **Registrar sólo los logs de warning a un archivo llamada warn.log**
- **Enviar sólo los logs de error a un archivo llamada error.log**

<br />
Use Winston y cree los siguientes transporters:

```
new winston.transports.Console({ level: 'info' }),
new winston.transports.File({ filename: 'warn.log', level: 'warn' }),
new winston.transports.File({ filename: 'error.log', level: 'error' })
```

En la consola aparecen todos los logs que puse y en los archivos guarda los warnings y errores, subí al repositorio los logs que se crearon cuando hice los tests para ver los mensajes generados.<br /><br />

**Mensajes INFO**<br /><br />
Puse los mensajes informativos, como por ejemplo "Base de datos conectada", "Nuevo cliente conectado" (cuando se ejecuta el socket), "Ingreso a la aplicación", etc.<br /><br>

**Mensajes WARN**<br /><br />
*Se graban en warn.log*<br />Algunos de los mensajes WARNING son por ejemplo si se intenta ingresar a la home de la app sin estar logueado  (```http://localhost:8080/index```) , o cuando un usuario cierra la sesion, (donde agrego el nombre de usuario y horario) en el mensaje, y cuando cierro el proceso de forma voluntaria.<br /><br>

**Mensajes ERROR**<br /><br />
*Se graban en error.log*<br />Se ejecuta cuando hay errores en alguna peticion, o si hay un error logueandose o iniciando la app.<br />Para probarlo borre una de las rutas de la API (la que levanta los mensajes del chat) y el error se grabo en error.log al ingresar a la app y fallar la carga de mensajes.<br />
<br />
<hr />
<br />

**Adjunte los archivos ```error.log``` y ```warn.log``` para que se puedan chequear los warnings y errores que recibi.**
