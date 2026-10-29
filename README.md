# Tarea: caja de mensajes

Interfaz basada en la imagen del profesor, siguiendo la configuración de
`clase_motor_plantilla`: módulos ES, Express, `express-handlebars`, vistas y layout.

## Ejecutar

Desde esta carpeta:

```powershell
npm install
npm start
```

Abre http://localhost:3000. Para reiniciar automáticamente al editar el servidor,
usa `npm run dev` en lugar de `npm start`.

## Variables y funcionamiento

- `username`: contiene `EJEMPLO`. Puedes cambiarlo en `src/index.js`.
- `cajaTexto`: contiene el texto recibido del formulario. Se envía también a la
  vista para conservarlo si hay un error de validación.
- `cajaMensajes`: arreglo de objetos con el usuario y el texto de cada mensaje.
- `publicidad` y `placeholder`: textos enviados desde Express a la vista.

1. `GET /` renderiza `index.handlebars` dentro de `layouts/main.handlebars`.
2. El formulario envía el campo `mensaje` mediante `POST /mensajes`.
3. `express.urlencoded` permite leerlo desde `req.body`.
4. El servidor rechaza mensajes vacíos o de más de 500 caracteres.
5. El mensaje válido se agrega a `cajaMensajes` y el servidor redirige a `/`.
6. Handlebars recorre el arreglo con `{{#each cajaMensajes}}` para mostrarlo abajo.
   Las expresiones `{{this.texto}}` escapan el HTML ingresado por el usuario.

Los mensajes se guardan en memoria: permanecen al actualizar la página, se
comparten entre quienes abran este servidor y se borran al reiniciarlo. Para esta
tarea no se utiliza una base de datos ni JavaScript en el navegador.

## Archivos

- `src/index.js`: servidor, variables, validación y rutas.
- `src/util.js`: ruta absoluta de la carpeta `src`, igual al ejemplo de clase.
- `src/views/layouts/main.handlebars`: estructura HTML y enlace al CSS.
- `src/views/index.handlebars`: interfaz y variables de Handlebars.
- `public/css/styles.css`: colores, distribución y adaptación a pantallas pequeñas.
