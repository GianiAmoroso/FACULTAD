# 🎵 Lab-Música: ¿qué tienen en común los hits de Spotify?

Análisis de datos de canciones de Spotify para identificar qué características musicales distinguen a los temas más populares del resto.

Trabajo práctico grupal del **Laboratorio de Métodos Cuantitativos Aplicados a la Gestión**, Tecnicatura Universitaria en Gestión y Análisis de Datos en Organizaciones (FCE, UBA), 2do cuatrimestre 2026.

---

## 📌 Pregunta de investigación

> **¿Qué patrones comparten las canciones más reproducidas de la historia reciente para replicar su éxito?**

**Motivación.** La industria musical invierte mucho en lanzamientos sin saber qué va a funcionar. Identificar qué tienen en común los temas más escuchados (tempo, energía, bailabilidad, duración) da a artistas y productores evidencia para decidir con datos y no solo con intuición. El análisis muestra asociaciones, no causas: el éxito también depende de factores que los datos no capturan, como el marketing.

**Hallazgos preliminares** (análisis en curso):

- Las canciones de **3,5 a 4,5 minutos** tienen la mayor popularidad promedio (35,3 puntos), seguidas por las de 2,5 a 3,5 minutos (33,8). Las cortas (< 2,5 min: 30,2) y las largas (> 4,5 min: 31,6) quedan por debajo.
- Los **hits** (popularidad > 70) son, en promedio, más bailables (*danceability* 0,625 contra 0,552 en las de baja popularidad), un poco más enérgicos (0,666 contra 0,641) y más alegres (*valence* 0,512 contra 0,479).

---

## 🗂️ Datos

### Dataset 1: Spotify Tracks Dataset (Audio Features)

| | |
|---|---|
| **Nombre** | Spotify Tracks Dataset (`spotify-tracks-dataset-detailed`) |
| **Fuente** | [Kaggle: Spotify Tracks Dataset (Audio Features)](https://www.kaggle.com/datasets/saichaitanyareddyai/spotify-tracks-dataset-audio-features) |
| **Cobertura** | 114.000 filas (unas 89.700 canciones únicas, porque una misma canción puede figurar en varios géneros), con su popularidad y características de audio |
| **Licencia** | CC0: Public Domain |

**Cómo obtenerlo:** descargarlo desde el [link de Kaggle](https://www.kaggle.com/datasets/saichaitanyareddyai/spotify-tracks-dataset-audio-features) (botón *Download*, requiere cuenta gratuita) y guardar el CSV en la carpeta `data/`.

#### Diccionario de datos

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

### Dataset 2: Spotify Global Music Dataset (2009–2025)

| | |
|---|---|
| **Nombre** | Spotify Global Music Dataset (2009–2025) |
| **Fuente** | [Kaggle: Spotify Global Music Dataset (2009–2025)](https://www.kaggle.com/datasets/wardabilal/spotify-global-music-dataset-20092025) |
| **Cobertura** | 8.582 canciones con datos del artista y del álbum. Aunque el nombre dice 2009–2025, incluye lanzamientos desde la década de 1950 hasta 2025 |
| **Licencia** | CC0: Public Domain |


**Cómo obtenerlo:** descargarlo desde el [link de Kaggle](https://www.kaggle.com/datasets/wardabilal/spotify-global-music-dataset-20092025) y guardar el CSV en la carpeta `data/`.

**Relación con el Dataset 1:** ambos tienen `track_id`, así que se pueden cruzar (`merge`) para sumar a cada canción su fecha de lanzamiento y los datos del artista.

#### Diccionario de datos

> La fuente no documenta las columnas: las descripciones se basan en los nombres y en cómo Spotify define esos campos.

**Canción**

| Variable | Tipo | Descripción |
|---|---|---|
| `track_id` | str | ID único de la canción en Spotify (clave para cruzar con el Dataset 1) |
| `track_name` | str | Nombre de la canción |
| `track_number` | int | Posición de la canción dentro del álbum (1 = primera) |
| `track_popularity` | int (0–100) | Popularidad de la canción, igual que `popularity` del Dataset 1 |
| `explicit` | bool | Si tiene letra explícita |
| `track_duration_min` | float | Duración en minutos |

**Artista**

| Variable | Tipo | Descripción |
|---|---|---|
| `artist_name` | str | Nombre del artista |
| `artist_popularity` | int (0–100) | Popularidad del artista, calculada a partir de la popularidad de todas sus canciones |
| `artist_followers` | int | Cantidad de seguidores del artista en Spotify |
| `artist_genres` | str | Géneros que Spotify le asigna al artista (Spotify asigna géneros a artistas, no a canciones) |

**Álbum**

| Variable | Tipo | Descripción |
|---|---|---|
| `album_id` | str | ID único del álbum en Spotify |
| `album_name` | str | Nombre del álbum |
| `album_release_date` | str (fecha) | Fecha de lanzamiento del álbum. Puede venir completa (`2015-03-20`) o solo con el año (`2015`) |
| `album_total_tracks` | int | Cantidad de canciones del álbum |
| `album_type` | str | Tipo de lanzamiento: `album`, `single` o `compilation` |

---

## 🔬 Metodología

**Hecho hasta ahora** (Dataset 1):

1. **Exploración inicial** de ambos datasets: primeras y últimas filas, estructura y columnas.
2. **Limpieza:**
   - Conversión de la duración de milisegundos a minutos (`duration_min`).
   - Eliminación de canciones repetidas por `track_id`: de 114.000 filas quedan unas 89.700 canciones únicas.
3. **Variables nuevas:**
   - `duracion_categoria`: Corta (< 2,5 min), Ideal (2,5–3,5), Estándar (3,5–4,5) y Larga (> 4,5).
   - `nivel_popularidad`: Baja (0–40), Media (41–70) y Alta / Hit (71–100).
4. **Resúmenes agrupados** con `groupby`: popularidad según la duración, y bailabilidad, energía y positividad según el nivel de popularidad.
5. **Gráficos:** distribución de la duración (histograma) y popularidad promedio por rango de duración (barras).

**Próximos pasos:**

- Gráfico de relación entre dos variables (por ejemplo, bailabilidad contra popularidad).
- Cruce con el Dataset 2 por `track_id`, para analizar la evolución por año de lanzamiento y el peso del artista (seguidores y popularidad).

Herramientas: Python (pandas, numpy, matplotlib, seaborn) en Google Colab.

---

## 📁 Estructura del repositorio

```
Lab-Musica/
├── README.md               ← este archivo
├── data/                   ← datasets
├── notebooks/
│   └── analisis_musica.ipynb   ← análisis completo en Python
├── figuras/                ← gráficos exportados del notebook
├── informe/
│   └── informe.pdf         ← informe académico con los resultados
└── presentacion/
    └── presentacion.pdf    ← diapositivas de la defensa
```

## ▶️ Cómo reproducir el análisis

1. Descargar los dos datasets desde Kaggle (links arriba).
2. Abrir `notebooks/analisis_musica.ipynb` en Google Colab.
3. Subir los CSV al panel de archivos de Colab con estos nombres: `spotify-tracks-dataset-detailed.csv` (Dataset 1) y `spotify_data clean.csv` (Dataset 2).
4. Ejecutar todas las celdas (*Entorno de ejecución → Ejecutar todas*).

---

## 👥 Integrantes

| Nombre | GitHub |
|---|---|
| Kiara Cusce | [@usuario](https://github.com/usuario) |
| Milagros Gonzalez | [@usuario](https://github.com/usuario) |
| Ian Chalverat | [@usuario](https://github.com/usuario) |
| Luka Ygelman | [@usuario](https://github.com/usuario) |
| Gianluca Amoroso | [@GianiAmoroso](https://github.com/GianiAmoroso) |

---

## 🤖 Uso de inteligencia artificial

Usamos IA como asistente en distintas etapas del trabajo. La interpretación de los resultados y las conclusiones son del grupo.

| Etapa | Herramienta | Uso |
|---|---|---|
| Análisis | _[herramienta]_ | Sintaxis de pandas (conversión a minutos, duplicados, `pd.cut`, `groupby`) y de gráficos con seaborn |
| Informe | _[Claude / Overleaf]_ | _[Ej.: redacción inicial en LaTeX]_ |
| Presentación | _[Canva IA / Gamma]_ | _[Ej.: diseño de diapositivas]_ |

Los *prompts* utilizados están documentados en el notebook, junto a cada celda.

---

## 🔗 Links

- 📓 Notebook en Colab: [abrir en Colab](https://colab.research.google.com/drive/1cru-iGU5_YV_iGRTIEpqLH1wKiQRVaVK)
- 📄 Informe: _[link]_
- 📊 Presentación: [ver en Canva](https://www.canva.com/design/DAHYGdB7fCY/WvV6k9WYQ0OdC-uf-KpF7g/edit)
