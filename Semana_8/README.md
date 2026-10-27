# Semana 8 - Aprendizaje No Supervisado: Segmentación de Clientes con K-Means

## 📌 Descripción del Proyecto

En esta entrega se aplica **clustering con K-Means** para descubrir segmentos latentes de clientes de un e-commerce a partir de su comportamiento de compra y de uso del sitio, **sin contar con etiquetas previas**.

El dataset (`dataset_segmentacion_clientes.csv`) contiene **700 clientes** sin valores nulos.

---

## 🎯 Pregunta Analítica y Objetivo

- **Pregunta:** ¿Qué grupos de clientes con comportamientos similares existen según su frecuencia de compra, ticket promedio, tiempo en el sitio, sensibilidad a descuentos y tasa de devoluciones?
- **Objetivo:** Determinar la cantidad adecuada de clusters con el **método del codo (k = 2 a 6)**, entrenar K-Means e interpretar los **centroides** para proponer acciones de negocio por segmento.

---

## 📊 Variables Utilizadas

| Variable | Descripción |
|---|---|
| `purchase_freq_month` | Frecuencia de compras por mes |
| `avg_basket_usd` | Ticket promedio por compra (USD) |
| `time_on_site_min` | Tiempo de permanencia en el sitio (minutos) |
| `discount_sensitivity` | Sensibilidad a descuentos (0 a 1) |
| `returns_rate` | Tasa de devoluciones (0 a 0.8) |

Las columnas `noise_gauss` y `noise_uniform` son **ruido aleatorio** y se excluyeron: al incluirlas, el coeficiente de silueta con k = 3 cae de 0.43 a 0.28.

---

## ⚙️ Metodología

1. **Exploración:** estadísticas descriptivas, histogramas y matriz de correlación.
2. **Escalado:** `StandardScaler`, necesario porque K-Means usa distancia euclídea y las variables tienen escalas muy distintas.
3. **Elección de k:** método del codo (inercia) para k = 2..6, complementado con el coeficiente de silueta.
4. **Modelado:** K-Means (`k-means++`, `n_init=10`, `random_state=42`).
5. **Interpretación:** centroides en unidades originales, visualización con PCA y boxplots por cluster.

---

## 📈 Resultados

### Método del codo

| k | Inercia | Silueta |
|---|---|---|
| 2 | 2088.9 | 0.40 |
| **3** | **1408.7** | **0.43** |
| 4 | 1173.4 | 0.43 |
| 5 | 997.7 | 0.42 |
| 6 | 762.5 | 0.46 |

La mayor caída de inercia ocurre entre k = 2 y k = 3 (≈33%), por lo que el **codo se ubica en k = 3**.

### Segmentos encontrados (k = 3)

| Segmento | Clientes | Frecuencia | Ticket | Tiempo en sitio | Sensib. descuentos | Acción sugerida |
|---|---|---|---|---|---|---|
| **Frecuentes / exploradores** | 230 | ~12/mes | ~180 USD | ~35 min | 0.54 (la más alta) | Promociones y fidelización |
| **Premium esporádicos** | 250 | ~1.9/mes | ~450 USD | ~6 min | 0.36 | Upselling premium, sin descuentos |
| **Ocasionales de bajo valor** | 220 | ~4/mes | ~90 USD | ~10 min | 0.38 | Activación y aumento del ticket |

### Segmentación fina (k = 6)

Cada segmento principal se divide en dos subgrupos:

- **Frecuentes:** "cazadores de ofertas" (sensibilidad ≈ 0.93) vs. **leales** que compran sin descuento (≈ 0.11).
- **Premium** y **ocasionales:** clientes con **devoluciones altas** (≈ 0.73) vs. **casi sin devoluciones** (≈ 0.04).

En este dataset el tiempo en el sitio no está asociado a la tasa de devoluciones (correlación ≈ 0).

---

## 🧾 Conclusiones

- El escalado fue indispensable para que todas las variables aportaran por igual a la distancia.
- K-Means identificó **3 segmentos principales** claramente separados, con perfiles y estrategias comerciales diferenciadas.
- La segmentación con k = 6 permite acciones más específicas, como atacar las devoluciones en los clientes premium, donde cada devolución es más costosa.

---

## 📁 Estructura

```
Semana_8/
├── Datos/
│   └── dataset_segmentacion_clientes.csv
├── Notebooks/
│   └── Tarea_Semana_8_kmeans.ipynb
└── README.md
```

## 🛠️ Tecnologías

Python · pandas · NumPy · scikit-learn · Matplotlib · Seaborn · Google Colab
