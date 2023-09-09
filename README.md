# Sistema de recomendación en tiempo real con PySpark, Spark Streaming y Apache Kafka.

## Objetivo
Recomendaremos canciones según las preferencias de los usuarios, pero se puede modificar el proyecto para recomendar otros temas o servicios.

Este proyecto se compone de varias etapas ya que se debe crear toda la infraestructura necesaria.

Cada usuario tiene sus preferencias musicales y en este proyecto recomendaremos nuevas canciones según las preferencias del usuario. De hecho, eso es exactamente lo que hace Sptify con los usuarios de su aplicación, para que los usuarios se suscriban al servicio pago de la compañía o mantengan su plan existente.

## Usaremos 2 flujos de datos:
- Stream_1: usaremos un conjunto de datos con miles de canciones. A partir de este conjunto de datos recomendaremos las canciones al usuario. Los datos fueron extraídos de este enlace -> https://research.atspotify.com/datasets
- Stream_2: extraigamos las preferencias musicales del usuario (yo) directamente desde Spotify con la API gratuita proporcionada por la empresa. Tendremos que crear una cuenta gratuita de Spotify, buscar algunas de tus canciones o artistas favoritos y darle a me gusta a algunas canciones para generar una gran cantidad de datos.

## ¿Qué es un Sistema de Recomendación?

Un sistema de recomendación es una herramienta o algoritmo para sugerir elementos, contenido o acciones que son relevantes para los usuarios en función de sus intereses, comportamientos, preferencias e historial de interacción.

Estos sistemas son ampliamente utilizados en plataformas en línea como comercio electrónico, servicios de transmisión, redes sociales y sitios de noticias, para ofrecer una experiencia personalizada a los usuarios y aumentar la satisfacción y el compromiso.

Los sistemas de recomendación se pueden clasificar en tres categorías principales:

- ***Filtrado colaborativo***: utiliza información sobre el comportamiento y las preferencias del usuario para encontrar patrones y hacer recomendaciones. Se puede dividir en filtrado colaborativo basado en memoria (como el enfoque de vecinos más cercanos) y filtrado colaborativo basado en modelos (como la factorización matricial). En este caso crearemos un sistema de filtrado colaborativo basado en memoria.

- ***Filtrado basado en contenido***: analiza las características de los elementos y recomienda elementos similares a aquellos en los que el usuario ha mostrado interés en el pasado. Por ejemplo, si un usuario vio muchas películas de acción, el sistema puede administrar otras películas del mismo género.

- ***Filtrado híbrido***: Combina diferentes técnicas de filtrado colaborativo y basado en contenido para mejorar la calidad de las recomendaciones. Este enfoque puede explotar las ventajas de ambas técnicas y compensar sus limitaciones.

Los sistemas de recomendación modernos también pueden utilizar técnicas de aprendizaje profundo e inteligencia artificial para mejorar la calidad de las sugerencias y adaptarse a los cambios en los intereses y preferencias de los usuarios. En el futuro traeré un modelo como este a este repositorio.

# Herramientas
Para trabajar con Spark Streaming utilizaremos Apache Spark, y para gestionar el streaming de datos utilizaremos Apache Kafka. Sin embargo, no será necesario instalarlo en tu máquina, ya que utilizaremos un contenedor Docker para Kafka.

## Arquitetura

<p align="center">
  <img width="1050" height="500" src="https://github.com/EricPassosScience/Monte_Carlo_Simulation-Time_Series/assets/97414922/57e4daa2-2bbe-400c-8a50-436d5668a287">
</p>

## Conectores

Para conectar Spark Streaming a Apache Spark, necesitamos conectores, que están disponibles a través de archivos .jar. A continuación se muestra la lista de conectores que estoy usando en este proyecto.: 
- https://mvnrepository.com/artifact/org.apache.spark/spark-sql-kafka-0-10_2.12/3.2.1
- https://mvnrepository.com/artifact/org.apache.kafka/kafka-clients/2.1.1
- https://mvnrepository.com/artifact/org.apache.spark/spark-token-provider-kafka-0-10_2.13/3.3.2
- https://mvnrepository.com/artifact/org.apache.commons/commons-pool2/2.8.0
- https://mvnrepository.com/artifact/org.apache.spark/spark-token-provider-kafka-0-10_2.12/3.1.2

Los conectores están en formato .jar. ¿Y qué es un archivo .jar? Significa "Archivo Java", es un archivo comprimido en el que se encuentra una clase Java, es decir, un programa Java.


No olvides acceder a tu cuenta de Spotify, acceder a la web del desarrollador, generar el Dashboard y luego crear la APP. Luego complete los campos Website y Redirect URLS. Esta dirección se usará en la autenticación de Spark Streaming.
## Fin
