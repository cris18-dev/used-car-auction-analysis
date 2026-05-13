# used-car-auction-analysis
## 2014–2015

Análisis exploratorio de 558,837 registros de subastas de vehículos usados en Estados Unidos, identificando patrones de precio, depreciación y comportamiento del mercado.

<img width="1220" height="630" alt="Dashboard" src="https://github.com/user-attachments/assets/ffff387e-552f-44f3-bafa-9955da38ff5d" />

---

## Dataset

| Atributo | Detalle |
|---|---|
| Fuente | [Kaggle – Vehicle Sales Data](https://www.kaggle.com/datasets/syedanwarafridi/vehicle-sales-data)|
| Registros | 558,837 transacciones |
| Período | 1982 – 2015 (concentrado en 2011–2015) |
| Variables | 16 columnas |

**Variables clave:**
- `year` — Año de fabricación del vehículo
- `make` / `model` / `trim` — Marca, modelo y versión
- `body` — Tipo de carrocería (Sedan, SUV, Coupe, etc.)
- `condition` — Condición del vehículo (escala 1–49)
- `odometer` — Kilometraje en millas
- `mmr` — Valor de mercado estimado (Manheim Market Report)
- `sellingprice` — Precio real de venta
- `saledate` — Fecha de la transacción

---

## Preguntas de negocio respondidas

1. ¿Qué marcas tienen el precio promedio de venta más alto?
2. ¿Cómo impacta el kilometraje en el precio de venta?
3. ¿La condición del vehículo determina linealmente el precio?
4. ¿Qué tipo de carrocería domina el mercado?
5. ¿Los vendedores venden por encima o por debajo del valor de mercado (MMR)?
6. ¿Cómo evolucionaron las ventas trimestralmente entre 2014 y 2015?

---

## Herramientas utilizadas

- **Microsoft Excel** — Tablas dinámicas, gráficos dinámicos, segmentadores (slicers), fórmulas avanzadas
- **Power Query** — Limpieza y transformación de datos
- **Excel Dashboard** — Visualización interactiva

---

##  Proceso de análisis

### 1. Limpieza de datos
- Eliminación de registros con valores nulos en `sellingprice` y `mmr`
- Corrección de caracteres especiales en campo `interior` (valores `â€"` reemplazados por vacío)
- Estandarización de fechas desde formato GMT a fecha Excel
- Agrupación de la variable `condition` (1–49) en 5 categorías: Muy baja / Baja / Media / Alta / Excelente
- Agrupación de `body` en 6 categorías principales: Sedan, SUV, Otros, Minivan, Hatchback, Coupe
- Creación de columna calculada `sellingprice - mmr` para medir desviación del precio de mercado

### 2. Análisis exploratorio
- Precio promedio por marca (52 marcas analizadas)
- Distribución de volumen por tipo de carrocería
- Correlación condición → precio promedio
- Depreciación por rango de odómetro (7 rangos de 50k millas)
- Diferencia precio real vs MMR por tipo de vendedor
- Tendencia trimestral 2014–2015

### 3. Visualización
- Dashboard interactivo con 5 KPIs y 6 gráficos dinámicos
- Gráfico combinado (barras + línea con eje secundario) 
  para rendimiento trimestral
- Slicers de filtrado por Año y Condición

---

## Hallazgos principales

**1. Depreciación acelerada en los primeros 100,000 millas**
El precio promedio cae un **68%** al pasar de 0–50k millas ($18,570) a 100–150k millas ($5,924). 
La depreciación se estabiliza cerca de $2,400–2,500 a partir de las 250,000 millas.

**2. Condición "Baja" tiene precio menor que "Muy baja"**
Los vehículos en condición Baja ($4,957) tienen precio promedio menor que los de condición Muy baja ($12,509). 
Esto sugiere que el rango 11–20 de la escala original captura vehículos con daño físico o siniestro, no simplemente antigüedad.

**3. El mercado vende sistemáticamente bajo el MMR**
La diferencia promedio entre precio real y MMR es **-$127**, indicando que en general los vendedores no recuperan el valor de mercado estimado. 
Los vendedores financieros (repos, title loans) presentan los mayores descuentos (-$1,200 promedio), mientras que los fabricantes OEM venden más cerca 
del valor de mercado (+$50 promedio).

---

## Estructura del repositorio
used-car-auction-analysis/
│
├── Cars_prices.xlsx   # Archivo principal con dashboard
├── dashboard_screenshot.png     # Captura del dashboard
└── README.md                    # Este archivo

## Dashboard

> Filtros interactivos disponibles por **Año** (2014/2015) 
> y **Condición** del vehículo (Muy baja → Excelente)

![Dashboard Preview](dashboard_screenshot.png)

---

## 👤 Autor

**Ana Lozano**  
Analista de Datos  
[LinkedIn](www.linkedin.com/in/ac-lozano) · 
[Kaggle](https://www.kaggle.com/analozano11)

---

*Dataset original: 
[Vehicle Sales Data – Kaggle]
(https://www.kaggle.com/datasets/syedanwarafridi/vehicle-sales-data)* 
