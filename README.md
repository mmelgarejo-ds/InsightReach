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

## Hallazgos clave

- **Ingresos** es la variable más predictiva: correlación 0.75 con frecuencia y 0.68 con gasto
- Clientes premium **triplican** ingresos y gasto vs no premium
- **Desequilibrio oferta-demanda:** Vegetariano (53 clientes/local) y Mariscos (70/local) vs Carnes (19/local)
- Top 25% por gasto concentra el **80.4% de membresías premium**
- Clientes 18-25 años lideran consumo de licor con **90.1%** vs 61.6% promedio

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
