# BSZInbox Magic

Es una herramienta para generar correos desechables o teporales , creado por javascrip , html y css donde arquiri una api gratuita mente ..

Link : https://toolapikey.foroactivo.com/h18-bszinbox-magic	
## ¿Qué hace esta aplicación?
La aplicación permite:

- Generar correos temporales de manera automática.
- Actualizar la bandeja de entrada para ver los correos recibidos en ese buzón.
- Mantener un historial de correos generados y sus respectivos mensajes.
- Mostrar una alerta si la API responde con un error (espera de 10 segundos).

## ¿Por qué se usa CORS Anywhere y la API TempMail.lol?

### CORS Anywhere
La aplicación utiliza `https://cors-anywhere.herokuapp.com/` para evitar restricciones de CORS al hacer solicitudes a la API de correos temporales. Esto permite que el navegador pueda comunicarse con `https://api.tempmail.lol/`, ya que muchas APIs bloquean las peticiones directas desde el frontend.

### API TempMail.lol
Se usa `https://api.tempmail.lol/` para generar correos electrónicos temporales y obtener los mensajes recibidos. Esta API proporciona:

- Creación de direcciones de correo temporales.
- Un identificador (token) asociado a cada correo para acceder a su bandeja de entrada.
- Listado de correos electrónicos recibidos en la bandeja temporal.

## Desglose del código

### HTML (Interfaz gráfica)

#### Estructura principal:

- Se define un contenedor `<div id="app">` donde Vue.js montará la aplicación.
- Se muestra el correo actual y botones para actualizar la bandeja o generar un nuevo correo.
- Se listan los correos recibidos y se almacena un historial de correos generados.

#### Elementos clave:

- `v-if="loading"` → Muestra "Generando correo..." mientras se obtiene uno nuevo.
- `v-else` → Muestra el correo actual y opciones una vez que ya se generó uno.
- `v-for` → Renderiza listas dinámicas como la bandeja de entrada y el historial.
- `v-show="showAlert"` → Muestra un mensaje de espera cuando la API falla.

### JavaScript (Lógica con Vue.js)

Usa Vue 3 en Composition API, con `setup()` y `ref()` para manejar el estado.

#### Variables Reactivas (`ref`)

```js
const email = ref('');
const token = ref('');
const emails = ref([]);
const loading = ref(true);
const history = ref([]);
const showAlert = ref(false);
let alertTimeout = null;
```

- `email` → Guarda el correo generado.
- `token` → Se usa para acceder a la bandeja.
- `emails` → Lista de correos recibidos en el buzón.
- `loading` → Indica si está cargando un nuevo correo.
- `history` → Guarda los correos generados y sus mensajes.
- `showAlert` → Muestra una alerta si ocurre un error.

### Generar un nuevo correo

```js
const generateEmail = async () => {
    try {
        const response = await axios.post('https://cors-anywhere.herokuapp.com/https://api.tempmail.lol/v2/inbox/create');
        email.value = response.data.address;
        token.value = response.data.token;

        history.value.push({ email: email.value, emails: [] });
        fetchInbox();
    } catch (error) {
        console.error('Error generating email:', error);
        if (error.message === "Request failed with status code 500") {
            showAlert.value = true;
            alertTimeout = setTimeout(() => {
                showAlert.value = false;
            }, 10000); // Espera 10 segundos
        }
    } finally {
        loading.value = false;
    }
};
```

- Hace una petición a la API para generar un nuevo correo.
- Guarda la dirección de email y el token en las variables reactivas.
- Agrega el correo al historial con un array vacío de emails.
- Llama a `fetchInbox()` para obtener los mensajes de la bandeja.
- Muestra una alerta de error si la API falla (y la oculta tras 10 segundos).

### Actualizar la bandeja de entrada

```js
const fetchInbox = async () => {
    if (!token.value) return;
    try {
        const response = await axios.get(`https://cors-anywhere.herokuapp.com/https://api.tempmail.lol/v2/inbox?token=${token.value}`);
        emails.value = response.data.emails;

        const currentHistory = history.value.find(item => item.email === email.value);
        if (currentHistory) {
            currentHistory.emails = emails.value;
        }
    } catch (error) {
        console.error('Error fetching inbox:', error);
    }
};
```

- Verifica si hay un token (correo generado).
- Solicita los correos de la bandeja con una petición GET a la API.
- Actualiza `emails` con la lista de correos obtenidos.
- Guarda los correos en el historial bajo el buzón correspondiente.

### Montaje Automático

```js
onMounted(generateEmail);
```

Cuando la página se carga, genera un correo automáticamente.

## Resumen General

- Al cargar la página, se genera un correo temporal automáticamente.
- El usuario puede generar otro correo manualmente si lo desea.
- Los correos recibidos se pueden consultar en la bandeja de entrada.
- El historial almacena los correos generados y sus respectivos mensajes.
- Si hay un error al generar un correo, aparece una alerta de espera de 10 segundos.
- Se incluyen botones para actualizar la bandeja y generar nuevos correos.
  
![image](https://github.com/user-attachments/assets/d08e4443-f285-4d42-a852-093a82e83654)

