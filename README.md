# Contrato pedagógico — Lic. Guillermo Ferreyra

Página de tres pasos para publicar con **GitHub Pages**:

1. Datos del estudiante.
2. Lectura del contrato.
3. Aceptación y envío.

## Cursos disponibles

El menú desplegable contiene únicamente:

- **Psicoanálisis I — viernes, turno tarde**
- **Psicoanálisis II — lunes, turno tarde**

## Importante

GitHub Pages muestra la página, pero no guarda respuestas. Para registrar los datos y la aceptación, el formulario debe conectarse con un **Google Form**.

La página ya está preparada para enviar directamente a Google Forms sin mostrar un segundo formulario incrustado.

---

## 1. Crear el Google Form

Creá un formulario titulado:

**Contrato pedagógico — Lic. Guillermo Ferreyra — Psicoanálisis I y II**

Agregá estas preguntas obligatorias, preferentemente en este orden:

1. **Apellido y nombre** — respuesta corta.
2. **Legajo** — respuesta corta.
3. **Correo institucional** — respuesta corta.
4. **Materia y turno** — lista desplegable:
   - Psicoanálisis I — viernes, turno tarde
   - Psicoanálisis II — lunes, turno tarde
5. **Aceptación** — casilla con una única opción:
   - Leí, comprendí y acepto el Contrato pedagógico, versión 24/07/2026.
6. **Versión del contrato** — respuesta corta. Puede quedar como dato oculto en la página.

En la pestaña **Respuestas**, vinculá el formulario con una hoja de cálculo.

---

## 2. Obtener los códigos `entry`

La forma más simple es usar un vínculo precompletado:

1. En Google Forms, abrí el menú de tres puntos.
2. Elegí **Obtener vínculo precompletado**.
3. Escribí datos de prueba en todas las preguntas.
4. Presioná **Obtener vínculo**.
5. Copiá la dirección generada.

La URL tendrá fragmentos similares a:

```text
entry.123456789=Nombre+de+prueba
entry.234567890=12345
entry.345678901=correo%40ejemplo.com
```

Cada `entry.XXXXXXXXX` corresponde a una pregunta.

En `index.html`, reemplazá:

```text
ENTRY_NOMBRE
ENTRY_LEGAJO
ENTRY_CORREO
ENTRY_MATERIA
ENTRY_ACEPTACION
ENTRY_VERSION
```

por los códigos `entry.XXXXXXXXX` correctos.

Ejemplo:

```html
<input id="nombre" name="entry.123456789" type="text" required>
```

---

## 3. Obtener la dirección de envío

Copiá la URL normal del Google Form. Suele verse así:

```text
https://docs.google.com/forms/d/e/FORMULARIO_ID/viewform
```

Transformala en:

```text
https://docs.google.com/forms/d/e/FORMULARIO_ID/formResponse
```

En `index.html`, reemplazá:

```javascript
const FORM_ACTION = "PEGA_AQUI_LA_URL_FORM_RESPONSE";
```

por la dirección terminada en `/formResponse`.

Ejemplo:

```javascript
const FORM_ACTION = "https://docs.google.com/forms/d/e/FORMULARIO_ID/formResponse";
```

Cuando termines, podés eliminar el bloque visible que dice **Configuración pendiente**.

---

## 4. Probar antes de publicarlo

1. Abrí `index.html` en el navegador.
2. Completá los datos.
3. Avanzá por las tres pantallas.
4. Presioná **Aceptar y enviar**.
5. Verificá que la respuesta aparezca en Google Forms y en la planilla vinculada.

No publiques la página hasta confirmar que todos los campos llegan correctamente.

---

## 5. Publicar con GitHub Pages

1. Creá un repositorio público llamado, por ejemplo, `contrato-psicoanalisis`.
2. Subí `index.html` y `README.md`.
3. Entrá en **Settings > Pages**.
4. Seleccioná:
   - Source: **Deploy from a branch**
   - Branch: **main**
   - Folder: **/(root)**
5. Guardá.

La dirección tendrá este formato:

```text
https://TU-USUARIO.github.io/contrato-psicoanalisis/
```

## Presentación en clase

Proyectá el enlace o un código QR y pediles:

> Completen primero sus datos, lean el contrato y, en la última pantalla, marquen la aceptación y presionen “Aceptar y enviar”.

## Control de versiones

Ante cambios importantes:

1. Modificá la fecha de versión en `index.html`.
2. Modificá el texto de aceptación.
3. Solicitá que los estudiantes vuelvan a aceptar la nueva versión.
