# InsightReach — Análisis Exploratorio de Clientes de Restaurantes

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat&logo=python&logoColor=white)

EDA sobre 30.000 clientes de restaurantes en ciudades de EE.UU., con integración
a la API de Yelp para cruzar demanda con oferta real.
Módulo 1 — Soy Henry Data Science AI.

---

## Problema de negocio

Identificar segmentos de clientes con mayor valor para restaurantes,
detectar nichos con alta demanda y baja oferta, y generar recomendaciones
accionables basadas en datos.

---

## Dataset

- 30.000 clientes · 17 columnas
- Variables clave: edad, ingresos, membresía premium, preferencias alimenticias, frecuencia de visita, gasto promedio
- Ciudad de análisis: **Chicago** (5.071 clientes · 16.9% del total)

---

## Pipeline

| Etapa | Contenido |
|---|---|
| Limpieza | Imputación de nulos con mediana por ciudad, corrección de valores imposibles |
| EDA | Distribuciones, correlaciones, análisis multi-ciudad |
| API Yelp | 200 restaurantes obtenidos · Rating bayesiano para corregir sesgos |
| Segmentación | 6 segmentos definidos por comportamiento y preferencias |

---

## Resumen ejecutivo

El análisis identifica un cliente premium claramente más valioso, un desequilibrio fuerte entre oferta y demanda por tipo de cocina, y un patrón de consumo en clientes jóvenes sin explotar comercialmente. Los tres hallazgos más relevantes:

1. **Ingresos es la señal más fuerte de valor comercial** — correlación 0,75 con frecuencia de visita y 0,68 con gasto promedio.

   <p align="center"><img src="figures/correlacion.png" alt="Matriz de correlación" width="70%"></p>

2. **La membresía premium triplica ingresos y gasto del cliente**, y el top 25% por gasto concentra el 80,4% de las membresías premium — el programa funciona, pero está concentrado en un segmento chico.

   <p align="center"><img src="figures/ingresos_membresia.png" alt="Ingresos por tipo de membresía" width="65%"></p>

3. **Hay un desequilibrio claro entre oferta y demanda por tipo de cocina**: 53 clientes por restaurante vegetariano y 70 por restaurante de mariscos, contra solo 19 por restaurante de carnes (muestra de 200 locales vía API de Yelp, ver límites abajo).

**Otro hallazgo:** clientes de 18-25 años lideran consumo de alcohol con 90,1% vs 61,6% del promedio general — patrón no explotado por ninguna oferta segmentada por edad en el mercado actual.

<p align="center"><img src="figures/alcohol_edad.png" alt="Consumo de alcohol por edad" width="70%"></p>

**Dato vs. hipótesis de negocio:** lo de arriba (correlaciones, proporciones, ratios cliente/local) es lo que muestran los datos. Las recomendaciones derivadas — expandir el programa premium, evaluar apertura de locales vegetarianos/de mariscos, o lanzar marketing segmentado por edad — son hipótesis de negocio a validar, no conclusiones del EDA en sí; están desarrolladas en el [`INFORME_EJECUTIVO.md`](INFORME_EJECUTIVO.md).

---

## Límites de la muestra y de la integración con Yelp

- El cruce oferta-demanda (53/70/19 clientes por local) sale de comparar los 30.000 clientes contra **200 restaurantes** obtenidos de la API de Yelp, filtrados a locales con 50+ reseñas para asegurar una muestra confiable — no es el universo completo de restaurantes del mercado, es una muestra.
- Esos ratios dependen del radio de búsqueda y los filtros usados contra la API; cambiarlos movería los números.
- Las correlaciones (0,75 y 0,68) son asociación estadística, no causalidad.
- Es un corte transversal — una foto en un momento dado, no una serie temporal — no muestra si estos patrones están creciendo, estables o cambiando.
- El análisis de ingresos/membresía usa como referencia Chicago (5.071 clientes, 16,9% del total); el resto de los hallazgos usan la base completa de 30.000.

---

**Informe ejecutivo** (hallazgos y recomendaciones de negocio, pensado para lectores no técnicos): [`INFORME_EJECUTIVO.md`](INFORME_EJECUTIVO.md).

---

## Segmentos identificados

| Segmento | Clientes | Gasto promedio |
|---|---|---|
| Premium Carnes | 629 | $38.89 |
| Vegetariano | 1.123 | — |
| Mariscos | 696 | — |
| Sin membresía | 3.169 | $15.69 |
| Digital | 1.375 | — |
| Sin preferencia | 859 | — |

---

## Stack

Python · Pandas · NumPy · Matplotlib · Seaborn · API Yelp

---

## Cómo reproducirlo

```bash
git clone https://github.com/mmelgarejo-ds/InsightReach.git
cd InsightReach
pip install -r requirements.txt
jupyter notebook
```

Correr `1_EDA_exploratorio.ipynb` y luego `2_integracion_api_yelp.ipynb` (requiere una API key propia de Yelp Fusion, no incluida en el repo).

---

## Autor

Mauricio Melgarejo · [LinkedIn](https://www.linkedin.com/in/mauricio-daniel-melgarejo-amaro-482596105/) · [GitHub](https://github.com/mmelgarejo-ds)
