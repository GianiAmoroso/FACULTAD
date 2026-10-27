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

| | |
|---|---|
| **¿Por qué vale la pena responderla?** | La industria musical invierte mucho en lanzamientos sin saber qué va a funcionar. Identificar qué tienen en común los temas más escuchados (tempo, energía, bailabilidad, duración) da a artistas y productores evidencia para decidir con datos y no solo con intuición. El análisis muestra asociaciones, no causas: el éxito también depende de factores que los datos no capturan, como el marketing. |
| **¿Qué respuesta encontramos?** | _Se completa al final del análisis_ |

---

## 🗂️ Dataset

| | |
|---|---|
| **Nombre** | _[A definir]_ |
| **Fuente** | _[Link. Ej.: Kaggle, Spotify API]_ |
| **Cobertura** | _[Período / región / cantidad de canciones]_ |
| **Licencia** | _[Según la fuente]_ |

**Cómo obtenerlo:** _[Instrucciones de descarga, o ruta al archivo en `data/`]_

### Diccionario de datos

| Variable | Tipo | Descripción |
|---|---|---|
| _ej.: `popularity`_ | int (0–100) | Popularidad de la canción en la plataforma |
| _ej.: `danceability`_ | float (0–1) | Qué tan apta es la canción para bailar |
| _ej.: `energy`_ | float (0–1) | Intensidad y actividad percibida |
| _ej.: `valence`_ | float (0–1) | Positividad musical (alegre vs. triste) |
| _ej.: `tempo`_ | float (BPM) | Velocidad estimada |
| _ej.: `duration_ms`_ | int | Duración en milisegundos |
| _ej.: `genre`_ | str | Género musical |
| _ej.: `year`_ | int | Año de lanzamiento |

> Ajustar esta tabla a las columnas reales del dataset elegido.

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
