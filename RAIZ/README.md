# UberX — Viajes Interplanetarios

Prototipo de aplicación móvil de reserva de viajes espaciales, construido únicamente con **HTML y CSS**. Sin JavaScript.

---

## Vista previa del flujo

```
Splash → Home → Explorar → Reserva → Pago → Confirmación
```

Cada destino tiene su propia cadena de pantallas, por lo que el tiquete final siempre refleja el destino elegido por el usuario.

---

## Estructura del proyecto

```
RAIZ/
├── ASSETS/
│   └── img/
│       ├── logouber.png
│       ├── luna.jpg
│       └── Marte.webp
├── CSS/
│   ├── app.css
│   └── others.css
├── SCREENS/
│   ├── 01-splash.html
│   ├── 02-home.html
│   ├── 03-travel-marte.html
│   ├── 03-travel-tierra.html
│   ├── 03-travel-eei.html
│   ├── 03-travel-luna.html
│   ├── 04-booking-marte.html
│   ├── 04-booking-tierra.html
│   ├── 04-booking-eei.html
│   ├── 04-booking-luna.html
│   ├── 05-payment-marte.html
│   ├── 05-payment-tierra.html
│   ├── 05-payment-eei.html
│   ├── 05-payment-luna.html
│   ├── 06-receipt-marte.html
│   ├── 06-receipt-tierra.html
│   ├── 06-receipt-eei.html
│   └── 06-receipt-luna.html
└── README.md
```

---

## Pantallas

| # | Archivo | Descripción |
|---|---------|-------------|
| 1 | `01-splash.html` | Pantalla de carga con logo animado |
| 2 | `02-home.html` | Inicio con destinos, búsqueda y navegación |
| 3 | `03-travel-[destino].html` | Mapa espacial y selección de nave |
| 4 | `04-booking-[destino].html` | Detalle de la nave y confirmación |
| 5 | `05-payment-[destino].html` | Selección de método de pago |
| 6 | `06-receipt-[destino].html` | Tiquete de confirmación del viaje |

Destinos disponibles: `marte` · `tierra` · `eei` · `luna`

---

## Interacciones CSS puras

Todas las interacciones están implementadas sin JavaScript, usando técnicas nativas de CSS:

### `:active` — efecto press
Las tarjetas de categoría en Home aplican `scale(0.93)` al ser presionadas, simulando feedback táctil.

### `:focus-within` — barra de búsqueda
El borde de la barra de búsqueda cambia a color dorado cuando el input interno está enfocado. Funciona porque el `input` está dentro del `label` que tiene el estilo.

### `input[type=radio]` + `:checked` — selección de nave y método de pago
Los radios están ocultos con `display: none`. Cada opción es un `<label>` asociado. Al hacer clic, CSS usa el selector `~` para detectar el radio marcado y resaltar el label correspondiente con borde dorado y un ✓ visible.

### `input[type=checkbox]` + `:checked` — botón swipe
El checkbox queda marcado permanentemente al hacer clic. CSS encadena tres cambios: el thumb se vuelve dorado, el texto desaparece y aparece el botón "Continuar al pago" con una transición de `opacity` + `translateY`.

### `:target` — modal de agregar tarjeta
El botón "Agregar nuevo método" apunta a `href="#modal-add"`. Esto activa `:target` en el overlay, que pasa de `opacity: 0` a `opacity: 1` y sube con `translateY`. El botón ✕ usa `href="#"` para cerrar el modal limpiando el hash.

### `@keyframes` — animaciones de entrada
- **Splash:** `splashDrop` — el logo y subtítulo caen desde arriba con rebote.
- **Receipt:** `fadeUp` — el check, título, subtítulo, tiquete y botones aparecen en secuencia con `animation-delay` escalonado.

---

## Sistema de diseño

Todas las variables de diseño están centralizadas en `:root` dentro de `app.css`:

```css
:root {
  --bg: #0d1117;        /* fondo principal */
  --bg-card: #161b22;   /* fondo de tarjetas */
  --bg-surface: #1c2230;/* fondo de superficies elevadas */
  --text: #ffffff;
  --muted: #8b949e;     /* texto secundario */
  --accent: #f0a500;    /* dorado — color de acción */
  --r: 16px;            /* radio de borde grande */
  --rs: 12px;           /* radio de borde pequeño */
  --font: 'DM Sans', sans-serif;
  --ease: 0.2s ease;
}
```

---

## Cómo abrir el proyecto

1. Clonar o descargar el repositorio
2. Abrir `SCREENS/01-splash.html` en el navegador
3. Navegar siguiendo el flujo de la aplicación

No requiere servidor, instalación ni dependencias.

---

## Tecnologías

- HTML5
- CSS3 (custom properties, flexbox, pseudo-clases, animaciones)
- Google Fonts — [DM Sans](https://fonts.google.com/specimen/DM+Sans) · [Syne](https://fonts.google.com/specimen/Syne)
