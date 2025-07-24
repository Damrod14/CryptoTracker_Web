# CryptoTracker Web

CryptoTracker Web es una aplicación web distribuida que permite consultar precios de criptomonedas en tiempo real, visualizar gráficas históricas, comparar activos y analizar tendencias mediante regresión lineal.

Este proyecto está dividido en **microservicios**, con backend en **Java** y frontend ligero en **HTML + JS**, desplegados en **Google Cloud**.

---

## Tecnologías utilizadas

- **Java 17** con `HttpServer` embebido
- **XChart** para generar gráficas en PNG
- **MySQL** para almacenamiento histórico
- **Google Cloud Compute Engine** para el despliegue
- **HTML + JavaScript** como frontend
- API pública: [CoinGecko](https://www.coingecko.com/)

---

## Estructura del Proyecto

- `WebServer.java`  
  Exposición de endpoints REST para consultar precios actuales (`/precios`, `/status`)

- `GraficoService.java`  
  Generación de gráficas PNG para variación de precios, comparaciones y regresión lineal  
  Endpoints: `/grafico`, `/graficoCompara`, `/regresion`

- `RecolectorPrecios.java`  
  Proceso programado que recolecta y almacena precios de 10 criptomonedas cada 10 segundos

- `index.html`  
  Interfaz web para interactuar con los servicios, alojada con NGINX

---

## Funcionalidades

- Consulta de precios actualizados
- Visualización de la variación en las últimas _N_ horas
- Comparación entre dos criptos
- Análisis con regresión lineal
- Frontend sencillo y directo
- Despliegue modular por microservicio

---

## Despliegue

Cada microservicio se despliega en su propia instancia de GCP:

- `RecolectorPrecios`: VM con Java + MySQL
- `GraficoService`: VM que expone gráficas en PNG
- `WebServer`: VM que entrega datos JSON
- `Frontend`: VM con NGINX

---
