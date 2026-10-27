# 🎵 Lab-Música

**Trabajo Práctico Grupal — Exploración, análisis y presentación de datos reales asistida por IA**

Laboratorio de Métodos Cuantitativos Aplicados a la Gestión
Tecnicatura Universitaria en Gestión y Análisis de Datos en Organizaciones
Facultad de Ciencias Económicas — Universidad de Buenos Aires
2do Cuatrimestre 2026

> 📅 **Entrega y defensa:** viernes 6 de noviembre de 2026, antes del inicio de la clase.

---

## 📌 Pregunta de investigación

> **¿Qué características musicales distinguen a las canciones más reproducidas en Spotify durante los últimos años del resto, y qué patrones podrían orientar decisiones de producción y lanzamiento?**

**¿Cuál es la pregunta?** ¿Qué patrones comparten las canciones más reproducidas de la historia reciente para replicar su éxito?
 
**¿Por qué vale la pena responderla?** La industria musical invierte mucho en lanzamientos sin saber qué va a funcionar. Identificar qué tienen en común los temas más escuchados (tempo, energía, bailabilidad, duración) da a artistas y productores evidencia para decidir con datos y no solo con intuición. El análisis muestra asociaciones, no causas: el éxito también depende de factores que los datos no capturan, como el marketing.
 
**¿Qué respuesta encontramos?**  _Se completa al final del análisis_ 

---

## 🗂️ Dataset

| | |
|---|---|
| **Nombre** | Spotify Tracks Dataset (`spotify-tracks-dataset-detailed`) |
| **Fuente** | [Kaggle: Spotify Tracks Dataset (Audio Features)](https://www.kaggle.com/datasets/saichaitanyareddyai/spotify-tracks-dataset-audio-features) |
| **Cobertura** | Canciones de Spotify de distintos géneros, con su popularidad y características de audio |
| **Licencia** | CC0: Public Domain |

**Cómo obtenerlo:** descargarlo desde el [link de Kaggle](https://www.kaggle.com/datasets/saichaitanyareddyai/spotify-tracks-dataset-audio-features) (botón *Download*, requiere cuenta gratuita) y guardar el CSV en la carpeta `data/`.

### Diccionario de datos

**Identificación**

| Variable | Tipo | Descripción |
|---|---|---|
| `track_id` | str | ID único de la canción en Spotify |
| `artists` | str | Artista/s; si hay más de uno, van separados por `;` |
| `album_name` | str | Nombre del álbum |
| `track_name` | str | Nombre de la canción |
| `track_genre` | str | Género musical |

**Éxito y formato**

| Variable | Tipo | Descripción |
|---|---|---|
| `popularity` | int (0–100) | Popularidad según Spotify. Se calcula por la cantidad de reproducciones y qué tan recientes son: 100 = lo más escuchado |
| `duration_ms` | int | Duración en milisegundos (÷ 60.000 = minutos) |
| `explicit` | bool | Si tiene letra explícita (`True`/`False`) |

**Características de audio** (las calcula Spotify analizando el sonido)

| Variable | Tipo | Descripción |
|---|---|---|
| `danceability` | float (0–1) | Qué tan bailable es, según ritmo, estabilidad del pulso y regularidad |
| `energy` | float (0–1) | Intensidad percibida: rápida, fuerte y ruidosa → cerca de 1; tranquila → cerca de 0 |
| `loudness` | float (dB) | Volumen promedio. Valores negativos, entre -60 y 0: más cerca de 0 = más fuerte |
| `speechiness` | float (0–1) | Cuánta voz hablada tiene. > 0,66 casi todo hablado (podcast); 0,33–0,66 mezcla (rap); < 0,33 música |
| `acousticness` | float (0–1) | Probabilidad de que sea acústica (sin instrumentos eléctricos) |
| `instrumentalness` | float (0–1) | Probabilidad de que no tenga voz. > 0,5 = probablemente instrumental |
| `liveness` | float (0–1) | Probabilidad de que sea en vivo (se detecta público). > 0,8 = probablemente en vivo |
| `valence` | float (0–1) | Positividad: cerca de 1 = alegre/eufórica; cerca de 0 = triste/enojada |
| `tempo` | float (BPM) | Velocidad en pulsos por minuto |
| `key` | int (-1 a 11) | Tonalidad: 0 = Do, 1 = Do#, 2 = Re… 11 = Si; -1 = no detectada |
| `mode` | int (0/1) | Modo: 1 = mayor (suele sonar alegre), 0 = menor (suele sonar triste) |
| `time_signature` | int (3–7) | Compás: pulsos por compás (4 = 4/4, el más común) |

---

## 📁 Estructura del repositorio

```
Lab-Musica/
├── README.md               ← este archivo
├── data/                   ← dataset (o instrucciones para descargarlo)
├── notebooks/
│   └── analisis_musica.ipynb   ← notebook de Colab, ejecutado completo
├── figuras/                ← gráficos exportados con plt.savefig()
├── informe/
│   ├── informe.pdf         ← informe académico final
│   └── overleaf.md         ← link al proyecto de Overleaf (si se usa LaTeX)
└── presentacion/
    └── presentacion.pdf    ← diapositivas (o link a la presentación)
```

---

## 🧭 Partes del trabajo

### Parte 1: Análisis en Python (Google Colab)

El notebook tiene que estar **ejecutado completo** y exportado como `.ipynb`. Cada celda de código va precedida por una celda Markdown que explica qué se hace y por qué.

- [ ] **3.1 Carga y exploración:** `.head()`, `.tail()`, dimensiones, `.dtypes`, cobertura, nulos, duplicados y `.describe()`
- [ ] **3.2 Pregunta de investigación:** celda Markdown con la pregunta, su motivación y la respuesta encontrada
- [ ] **3.3 Transformaciones:** al menos **2 transformaciones justificadas** y **2 estadísticos agrupados** con `.groupby()`
- [ ] **3.4 Gráficos:** mínimo **3 gráficos de tipos distintos**, con título, ejes etiquetados e interpretación:
  - [ ] Evolución temporal o distribución (línea, histograma o boxplot)
  - [ ] Comparación entre categorías (barras)
  - [ ] Relación entre dos variables (dispersión o líneas superpuestas)
- [ ] Indicar qué celdas contaron con asistencia de IA y qué *prompt* se usó

### Parte 2: Informe académico (PDF, 3 a 5 páginas)

- [ ] §1 Resumen (5–8 líneas)
- [ ] §2 Introducción (½ pág.)
- [ ] §3 Datos y metodología (½ pág.)
- [ ] §4 Resultados (1–2 pág.)
- [ ] §5 Conclusiones (½ pág.)
- [ ] §6 Reflexión metodológica (¼ pág.)
- [ ] §7 Bibliografía (opcional)
- [ ] Revisión intragrupal (obligatoria)
- [ ] Validación externa con otro grupo (recomendada)

Redacción en tercera persona o impersonal. El informe tiene que entenderse sin abrir el notebook.

### Parte 3: Presentación con IA

- [ ] Diapositivas (6 a 10) hechas con Canva IA, PowerPoint Copilot, Gamma u otra herramienta similar
- [ ] Exposición de **5 a 7 minutos** (10 como máximo, contando las preguntas), con todos los integrantes conectados
- [ ] *(Opcional)* Video de 2 a 4 minutos **o** sitio web con los gráficos, los resultados y las conclusiones

---

## 👥 Integrantes

| Nombre | N° de registro | Usuario de GitHub |
|---|---|---|
| _[Nombre Apellido]_ | _[XXXXXX]_ | [@usuario](https://github.com/usuario) |
| _[Nombre Apellido]_ | _[XXXXXX]_ | [@usuario](https://github.com/usuario) |
| _[Nombre Apellido]_ | _[XXXXXX]_ | [@usuario](https://github.com/usuario) |
| _[Nombre Apellido]_ | _[XXXXXX]_ | [@usuario](https://github.com/usuario) |
| _[Nombre Apellido]_ | _[XXXXXX]_ | [@usuario](https://github.com/usuario) |

> ⚠️ **Todos los integrantes tienen que tener commits significativos.** La cátedra revisa el historial: quien no tenga commits no acredita el trabajo grupal.

---

## 🤖 Uso de IA

El trabajo usa IA como asistente en todas las etapas. La interpretación y el criterio analítico son responsabilidad del grupo.

| Etapa | Herramienta | Para qué se usó |
|---|---|---|
| Análisis | _[Claude / ChatGPT]_ | _[Ej.: sugerir transformaciones y tipos de gráfico]_ |
| Informe | _[Claude / Overleaf]_ | _[Ej.: redacción inicial en LaTeX]_ |
| Presentación | _[Canva IA / Gamma]_ | _[Ej.: diseño de diapositivas]_ |

Los *prompts* usados en el análisis están documentados en el notebook, junto a cada celda.

---

## 🔗 Links

- 📓 Notebook en Colab: _[link]_
- 📄 Proyecto en Overleaf: _[link]_
- 📊 Presentación: _[link]_
- 🎬 Video / 🌐 Sitio web (opcional): _[link]_

---

## ✅ Checklist de entrega (6/11/2026)

- [ ] Notebook `.ipynb` **ejecutado** en el repositorio
- [ ] PDF del informe en el repositorio
- [ ] Dataset o instrucciones para descargarlo
- [ ] Presentación (archivo o link) en el repositorio
- [ ] Commits de **todos** los integrantes
- [ ] PDF único de entrega en el campus, con la portada (nombres, registros, usuarios de GitHub y link al repo) y el link a la presentación, el video o el sitio
