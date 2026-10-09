# Temporizador de presentaciones

[English](README.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [हिन्दी](README.hi.md) | [Español](README.es.md) | [Français](README.fr.md) | [العربية](README.ar.md) | [বাংলা](README.bn.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Bahasa Indonesia](README.id.md) | [Deutsch](README.de.md) | [한국어](README.ko.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md)

Un temporizador de una sola página para que cada persona se presente por turnos en reencuentros y eventos similares. Basta con abrir `index.html` en un navegador: sin instalación, servidor ni conexión a internet.

## Uso

1. Abre `index.html` en un navegador (Safari / Chrome).
2. En la pantalla de ajustes: carga un CSV (consulta `sample/participants.csv` o usa «Cargar ejemplo»), marca la asistencia de cada persona, ordena por cualquier campo, define el título / tiempo por persona / tratamiento / idioma y prueba los sonidos.
3. Pulsa «Ir al temporizador» (esto también activa el audio).
4. Usa el temporizador:

| Acción | Efecto |
|---|---|
| `Espacio` / botón Iniciar | Inicia a la siguiente persona (con aplausos) |
| Clic en un nombre de la lista de la derecha | Inicia a esa persona; quienes iban antes pasan a «Omitidos» |
| Clic en un nombre de «Omitidos» | Inicia a esa persona |
| Desmarcar «Presente» en «Omitidos» | Tras confirmar, se marca como ausente y se quita de la lista (el temporizador sigue) |

Quedan 10 s: un tic por segundo · quedan 3 s: pitidos rápidos · 0 s: explosión y etiqueta «¡Se acabó el tiempo!». Arriba a la derecha se muestra el tiempo total transcurrido y, en la columna derecha, las 10 personas siguientes.

## Formato CSV

La primera fila es el encabezado. Se detecta UTF-8 y Shift_JIS automáticamente. Las columnas de nombre y tratamiento se eligen según el encabezado (p. ej. `nombre`, `tratamiento`) y se pueden cambiar en los ajustes. Si la celda de tratamiento está vacía, se usa el tratamiento por defecto.

```csv
name,honorific,group,year
Alex Morgan,,A,2001
Sam Rivera,Dr.,B,2001
```

## Idiomas

16 idiomas: cámbialo con «Idioma» en la pantalla de ajustes (al principio se usa el idioma del navegador y tu elección se guarda). Los textos, el título y el tratamiento por defecto, los datos de ejemplo y la posición del tratamiento (antes/después del nombre) siguen el idioma; el árabe usa un diseño de derecha a izquierda. Las traducciones no han sido revisadas por hablantes nativos: edita `I18N` en `index.html` para corregirlas. Para añadir un idioma, agrega entradas en `LANGS`, `I18N` y `SAMPLE_NAMES`.

## Móvil

Diseños para móviles en vertical y horizontal. En iPhone, el interruptor de silencio apaga el sonido. Abrir el archivo desde la app Archivos es lo más fiable; con GitHub Pages basta con abrir una URL.

## Estructura

```
.
├── index.html            # app (HTML / CSS / JavaScript in one file)
├── sample/
│   └── participants.csv  # sample list
├── README.md             # + README.<lang>.md (16 languages)
└── LICENSE               # MIT
```

`index.html` lo contiene todo: el diccionario de idiomas, un analizador de CSV, la pantalla de ajustes, la síntesis de sonidos con Web Audio (sin archivos de audio), la lógica del temporizador (basada en marcas de tiempo, sin desviarse) y la pantalla de ejecución. Los ajustes y el progreso se guardan automáticamente en `localStorage`.

Licencia: [MIT](LICENSE)
