# ⚔️Crossover de Volumen Industrial

Este proyecto implementa una consulta SQL que detecta acumulación institucional a nivel industria, identificando momentos en los que el volumen total negociado supera significativamente su promedio histórico justo antes de un posible cambio de tendencia.

La lógica está inspirada en análisis técnico y flujo de capital institucional, aplicada de forma agregada por sector.

## 🧠Idea principal

El Crossover de Volumen Industrial busca responder a esta pregunta:

- ¿Cuándo una industria completa empieza a mostrar un volumen anormalmente alto, anticipando un cambio de tendencia?

Para eso:
- Se suma el volumen diario de todos los tickers de una misma industria.
- Se compara contra su promedio histórico reciente.
- Se detectan picos de volumen que suelen preceder movimientos relevantes en precios (ej. cruce de la SMA 50).

## 📈Valor de negocio

- Detecta acumulación institucional masiva
- Permite anticipar rotaciones sectoriales

- Útil para:
  - estrategias top-down
  - filtros previos a señales técnicas
  - análisis macro / sectorial cuantitativo

## 🗄️Estructura de datos esperada

El script asume la existencia de las siguientes tablas:
- precios_diarios
- campo	descripción
- ticker_id	Identificador del activo
- fecha	Fecha de cotización
- volume	Volumen negociado
- tickers
- campo	descripción
- ticker_id	Identificador del activo
- industria	Industria o sector

## ⚙️Lógica de la consulta

Agrupa el volumen diario por industria y fecha

Calcula:
- vol_total: volumen total diario de la industria
- vol_hist: promedio histórico de volumen (ventana móvil)

Filtra casos donde:
- el volumen actual es al menos el doble del promedio histórico

## 🔎Interpretación de resultados

- Señal fuerte: volumen industrial ≥ 2× su promedio reciente

Suele anticipar:
- quiebres de medias móviles (ej. SMA 50)
- cambios de régimen en el sector
- No es una señal de entrada directa, sino un detector de contexto

## 🚀Posibles extensiones

- Integrar directamente el cruce de SMA 50
- Normalizar volumen por capitalización
- Ajustar ventana temporal dinámicamente
- Visualizar resultados en dashboards (Power BI / Tableau / Python)

## 📝Notas

- La ventana de 20 días y el multiplicador ×2 son parámetros ajustables
- Pensado para bases de datos con histórico diario consistente
- Ideal como módulo dentro de un pipeline cuantitativo más grande

## 👤Autora
Flavia Hepp Proyecto de SQL aplicó un análisis de riesgo basado en eventos.

***
📊 A veces, el cambio de tendencia no empieza en el precio… empieza en el volumen.

---

Hay una señal que me parece especialmente interesante:

👉 Cuando el volumen de toda una industria se dispara por encima de su promedio histórico

Y no en cualquier momento…
sino justo antes de un cambio en la tendencia.

---

🔍 Lo que analicé:

* Volumen total agregado por industria
* Promedio histórico reciente
* Detección de picos (cuando el volumen es 2x el promedio)

---

💡 ¿Qué significa esto?

Cuando ves un aumento masivo de volumen a nivel sectorial:

* No es retail
* No es ruido
* Es capital grande moviéndose

👉 Posible acumulación institucional

---

🧠 Insight clave:

Antes de que el precio cambie de tendencia…

👉 alguien ya está posicionándose

Y eso se refleja primero en el volumen, no en el precio.

---

🚀 ¿Por qué importa?

Porque te permite adelantarte a movimientos relevantes:

* Detectar cambios de tendencia sectorial
* Identificar acumulación institucional
* Construir señales tempranas para modelos
* Mejorar timing de entrada

---

📈 Aplicaciones:

* Estrategias de momentum por industria
* Rotación sectorial
* Feature engineering en modelos cuantitativos
* Análisis de flujos de capital

---

🧠 Takeaway:

El precio muestra el resultado…

👉 el volumen muestra la intención.

Y cuando esa intención aparece a nivel industria,
la señal es mucho más fuerte.

---

Estoy trabajando en insights combinando SQL + lógica cuantitativa para detectar este tipo de patrones.

Si te interesa este enfoque, conversemos 👇

#DataScience #Quant #Finance #Trading #MachineLearning #SQL #Investing
