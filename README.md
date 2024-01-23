# TFM-Deteccion-de-topicos-argumentada

Este repositorio contiene un conjunto de herramientas y servicios para analizar y explorar temas en subreddits de Reddit. La aplicación utiliza FastAPI para la creación de una API web que permite realizar búsquedas en subreddits específicos y obtener noticias relacionadas con los temas identificados. Además, se incluyen funcionalidades para visualizar resultados y obtener explicaciones generadas automáticamente sobre los temas.

## Requisitos
Antes de ejecutar la aplicación, asegúrese de tener las siguientes bibliotecas instaladas en su entorno de Python:

```
pip install fastapi uvicorn praw numpy asyncpraw pandas matplotlib seaborn nltk gensim glob2 wordcloud
pip install scikit-learn umap-learn sentence-transformers GoogleNewsPy newspaper3k plotly openai requests
```

# Ejecución
1. Clone el repositorio:

```
git clone https://github.com/tuusuario/repo.git
cd repo
```

2. Configure sus credenciales de la API de Reddit en el código. Para ello complete los campos "user_name" y "password" en las siguientes líneas de código:

```
 reddit = praw.Reddit(client_id='L6VqhKkwJZHd2cR9mVUHXA', client_secret='I88aFVtUvDJzfHbMGqbiIBmt0XdVDw', user_agent='redditdev scraper by u/odon_pedrosa', username="", password="")

    asyncreddit = asyncpraw.Reddit(client_id='L6VqhKkwJZHd2cR9mVUHXA', client_secret='I88aFVtUvDJzfHbMGqbiIBmt0XdVDw', user_agent='redditdev scraper by u/odon_pedrosa', username="", password="")
```

3. Ejecute la aplicación:

```
uvicorn nombre_del_archivo:app --reload
```

La aplicación estará disponible en http://127.0.0.1:8000. Puede acceder a la interfaz Swagger para probar las API y sus endpoints.

## Uso de la API

La API consta de 4 funciones diferentes que, en su conjunto, abarcan todo el proceso de la detección de tópicos argumentada en redes sociales. Estas funciones son:
  
  1. Detección de tópicos en reddit.
  2. Obtención de noticias relacionadas con un tópico dado.
  3. Visualización de noticias con mapa de calor dinámico.
  4. Obtención de una explicación sobre el tema dado.

### 1. Detección de tópicos en Reddit.

Endpoint: /api/Search
Parámetros:
* Search: Nombre del subreddit a analizar.

Ejemplo de Uso:
```
curl -X 'GET' \
  'http://127.0.0.1:8000/api/Search?Search=python' \
  -H 'accept: application/json'
```

### 2. Obtener noticias relacionadas a un tópico

Endpoint: /api/news
Parámetros:
* n_topic: Número del tópico a explorar.

Ejemplo de Uso:
```
curl -X 'GET' \
  'http://127.0.0.1:8000/api/news?n_topic=0' \
  -H 'accept: application/json'
```

### 3. Visualización de mapa de calor
Endpoint: /heatmap

Ejemplo de Uso:
Abra http://127.0.0.1:8000/heatmap en su navegador para visualizar un mapa de calor de las noticias relacionadas.

### 4. Obtener la explicación de un tópico
Endpoint: /api/explanation

Ejemplo de Uso:
```
curl -X 'GET' \
  'http://127.0.0.1:8000/api/explanation' \
  -H 'accept: application/json'
```

### Notas adicionales
* Antes de utilizar la función related_news, asegúrese de ejecutar la función Search para obtener temas.
* Asegúrese de tener configuradas las credenciales de OpenAI para usar la función get_explanation.




  
