# 📊Rendimiento Ajustado al Riesgo Específico por Acción

(Sharpe Simple Sectorial – 30 días)

## 📌Descripción general

Este proyecto implementa un modelo simplificado de rendimiento ajustado por riesgo a nivel de acción, inspirado en el Ratio de Sharpe, con foco en comparar acciones dentro de su propio sector.

El objetivo es identificar qué acciones ofrecen la mejor calidad de rendimiento, es decir, mayor retorno promedio por cada unidad de volatilidad experimentada, en una ventana móvil de 30 días.

A diferencia de métricas puramente direccionales, este enfoque prioriza la eficiencia del movimiento del precio, no solo su magnitud.

## 🎯Pregunta que responde

- ¿Qué ticker ofrece el mejor rendimiento promedio a 30 días en su sector por cada unidad de volatilidad asumida?

Esto permite distinguir entre:

- Acciones que suben “ordenadamente”

- Acciones que suben con alta inestabilidad (ruido, riesgo específico)

## 🧠Insight clave

Un ratio Sharpe simple alto indica:
- Rendimientos consistentes
- Volatilidad controlada
- Menor riesgo específico no compensado

Estas acciones suelen ser candidatas ideales para:
- Rotación sectorial
- Posiciones core
- Estrategias long-only con control de riesgo
- Ranking relativo dentro de un sector

## 🧮Metodología

Para cada ticker, en los últimos 30 días:

- Rendimiento promedio

Rendimiento=AVG(𝐶𝑙𝑜𝑠𝑒−𝑂𝑝𝑒𝑛/𝑂𝑝𝑒𝑛)

- Riesgo específico (volatilidad)

Riesgo=STDEV(𝐶𝑙𝑜𝑠𝑒−𝑂𝑝𝑒𝑛/𝑂𝑝𝑒𝑛)

- Ratio Sharpe simplificado

Sharpe Simple=Rendimiento promedio/Volatilidad


Solo se consideran acciones con volatilidad positiva para evitar distorsiones.

📊 Output del modelo

La consulta devuelve:
- ticker_id
- sector
- rendimiento_promedio
- volatilidad_riesgo
- ratio_sharpe_simple

Ordenado de mayor a menor por calidad riesgo-retorno.

## 💼Valor de negocio

Este modelo permite:
- Comparar acciones más allá del retorno bruto
- Detectar líderes silenciosos dentro de cada sector
- Evitar acciones con retornos “inflados” por volatilidad extrema
- Mejorar la asignación de capital sectorial

Servir como filtro previo para:
- Stock picking
- Backtesting
- Modelos multifactoriales

## ⚠️Consideraciones

- Es una versión simplificada del Sharpe Ratio (no usa tasa libre de riesgo).
- Sensible a ventanas temporales: 30 días captura momentum reciente, no calidad estructural.
- Ideal como ranking relativo, no como métrica absoluta aislada.

## 🔗Dependencias de datos

- tickers
- precios_diarios
- Fechas consistentes y sin gaps significativos

## 🚀Extensiones posibles

- Normalizar el ratio por sector
- Combinar con métricas de cola (kurtosis)
- Evaluar estabilidad del Sharpe en ventanas móviles
- Usarlo como input para scoring multifactorial

## 👤Autora
Flavia Hepp Proyecto de SQL aplicó un análisis de riesgo basado en eventos.
