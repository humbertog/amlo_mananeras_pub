# Resultados del modelo LDA (Latent Dirichlet Allocation) aplicado a las conferencias matutinas de AMLO

Este repositorio contiene únicamente los resultados que se presentan en el sitio y no el código.

El algoritmo  MALLET (http://mallet.cs.umass.edu/) es utilizado, mediante la interfaz de Gensim (Python), para descubrir los temas en las conferencias. Cada conferencia es un documento y sólo las intervenciones de AMLO son tomadas en cuenta. El preprocesamiento básico de los datos de texto, incluye:
- eliminación de caracteres especiales
- creación de unigramas y bigramas
- eliminaión de stopwords, palabras muy poco frecuentes y muy frecuentes: palabras con bajo contenido semántico

El número de temas en el modelo LDA se establece en 65 con α = 40 (parámetro de dispersión de temas en los documentos).

Las transcripciones de las conferencias están disponibles en línea en el sitio web del Gobierno y se revisan periódicamente.
raspado y puesto en formato csv por https://github.com/NOSTRODATA/conferencias_matutinas_amlo

Para StreamGraph (https://en.wikipedia.org/wiki/Streamgraph), la distribución de temas se suaviza (7 días) mediante una ventana gaussiana, lo que le da una mejor presentación visual. Cada documento se limita a los 3 temas para diferenciar mejor los temas en los documentos (Tareas pendientes: esto se puede lograr utilizando valores α más pequeños).

Versión en artículo de Punto Decimal: 13/05/2021


## Notas sobre el procesamiento del texto

 - filter_extremes(no_below=10, no_above=.75,...) : se eliminan palabras que aparecen en menos de 10 documentos (conferencias) y aquellas que aparecen en más del 75% de los documentos. Las primeras son muy específicas, las segundas muy generales por lo que no aportan mucho significado, pero reduce significativamentela complejidad del problema. 

- Otras palabras que se eliminan  (stopwords):
  nltk.corpus.stopwords.words("spanish") +
  ["va", "van", "ahí", "si", "sí", "vamos", "día", "hoy", "buenos", "días", "gracias", "conferencia",
  "pues", "voy", "hace", "mañana", "ayer", "ir", "creo", "iba", "semana", "quién", "ahora", "informar",
  "informamos", "informaremos", "informo", "informarles", "lunes", "martes", "miércoles", "jueves",
  "viernes", "sábado", "domingo", "entonces", "aquí", "así", "país", "muchas", "ah", "buen", "sé",
  "dije", "existe", "dicen", "dice", "quieren", "quiere", "señor", "arriba", "abajo",
  "después", "allá", "iban", "mil", "sido", "miren", "imagínense"]

- Palabras que no se eliminan, a pesar de su alta frecuencia (más del 75% de los documentos):
  ['ayudar','presupuesto','empresas','respeto','dinero', 'austeridad',
  'corrupción', 'apoyo', 'política', 'pesos', 'estados_unidos',
  'proceso', 'vida', 'recursos', 'mil_millones']
  

## Bibliotecas:
- Gensim: Topic modelling for Humans (https://radimrehurek.com/gensim/)
- MALLET:  MAchine Learning for LanguagE Toolkit (http://mallet.cs.umass.edu/)
- NLTK: Natural Language ToolKit (https://www.nltk.org/)
- D3: Data Driven Documents (https://d3js.org/) para las gráficas




