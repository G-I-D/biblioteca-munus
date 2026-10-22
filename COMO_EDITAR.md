# Cómo editar el calendario y las guías desde GitHub

Todo se edita aquí, en GitHub, sin tocar el código pegado en Canva.
Después de guardar (**Commit changes**) espera 1-2 minutos y recarga la página.

> Para editar un archivo: ábrelo y pulsa el lápiz ✏️ (arriba a la derecha).
> Para subir una foto: entra a la carpeta → **Add file → Upload files**.

Reglas del formato (si algo falla, casi siempre es esto):
- Los textos van entre comillas `"así"`.
- Entre un elemento y otro va una coma `,` — pero **no** después del último.
- Fechas siempre `AAAA-MM-DD`, por ejemplo `2026-11-06`.
- `*palabra*` se ve en dorado/cursiva.
- Si la página no cambia, pega el archivo en <https://jsonlint.com> para encontrar el error.

---

## 📅 Calendario — `calendario/calendario.json`

### Foto de cada mes
1. Sube la foto a la carpeta `calendario/fotos/` con el nombre del mes, por ejemplo `2026-11.jpg`
   (usa .jpg o .webp, idealmente de menos de 500 KB).
2. En `calendario.json`, dentro de `"fotos"`, escribe su nombre:
   ```json
   "2026-11": "fotos/2026-11.jpg",
   ```
   Para quitarla, deja `""`.

### Agregar, mover o quitar un evento
Cada evento dentro de `"eventos"` se ve así:
```json
{
  "inicio": "2026-11-06",
  "fin": "2026-11-07",
  "cat": "modelo",
  "icono": "laurel",
  "confirmado": true,
  "titulo": "Lanzamiento del modelo 2027",
  "lugar": "Universidad de La Sabana · Auditorio David Mejía",
  "hora": "4:00 p. m.",
  "descripcion": "Qué es el evento.",
  "equipo": ["Junta Directiva 2027"],
  "tareas": ["Vestimenta formal", "Llega 30 minutos antes"],
  "enlace": "https://link-de-inscripcion-o-tiquetes"
}
```
- **Cambiar la fecha:** edita `"inicio"` (y `"fin"` si dura varios días; si es un solo día borra la línea `"fin"`).
- **Quitar un evento:** borra desde su `{` hasta su `},`.
- **Agregar uno:** copia un evento completo y pégalo debajo, separado por coma.
- **`"cat"`** (color): `impacto`, `modelo`, `capacitacion` u `otros`.
- **`"icono"`**: `laurel`, `globo`, `manos`, `libro`, `bandera`, `pluma`, `pin`, `reloj`, `equipo`, `cal`, `ticket`.
- **`"confirmado"`**: `false` muestra la etiqueta "Por confirmar".
- **`"enlace"`** (opcional): a dónde lleva el botón "Quiero ir". Sin enlace, abre WhatsApp.

### Otros datos del mismo archivo
- `"countdowns"`: las dos cuentas regresivas (fecha y texto).
- `"festivos"`: días festivos (`"2027-03-22": "Día de San José"`).
- `"meses"`: primer y último mes que muestra el calendario.
- `"redes"`, `"whatsapp"`, `"correo"`: links de contacto (cambia los `"#"` por los links reales).
- `"notasIzquierda"`, `"notasDerecha"`: los post-its.
- `"mapas"`: link de Google Maps de cada lugar.

---

## 📚 Guías de comité — `guias-comites/guias.json`

- `"fechas"`, `"titulo"`, `"lema"`, `"kicker"`: los textos de arriba de la página.
- Cada libro:
  ```json
  {
    "nombre": "DISEC",
    "tema": "Prevención de la escalada militar y seguridad marítima.",
    "etiquetas": ["Individual"],
    "enlace": "https://www.canva.com/design/.../view",
    "lomo": "lomos/08-disec.webp"
  }
  ```
- **Poner el link de una guía:** pégalo en `"enlace"`. Vacío (`""`) = "Guía próximamente".
- **Cambiar la imagen del lomo:** sube la nueva imagen a `guias-comites/lomos/` y escribe su nombre en `"lomo"`
  (proporción vertical 200 × 943 px, como las actuales).
- **Agregar / quitar un comité:** copia o borra un bloque `{ ... }` dentro de `"libros"`.
- **Dos libros pegados** (como Cumbre Global): `{ "par": [ {libro}, {libro} ] }`.
- **Secciones:** cada `{ "nombre": "SGA ...", "libros": [...] }` es un estante.
