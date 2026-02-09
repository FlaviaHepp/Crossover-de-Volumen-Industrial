# Crossover-de-Volumen-Industrial
Crossover de Volumen Industrial

Crossover de Volumen Industrial

Este proyecto implementa una consulta SQL que detecta acumulación institucional a nivel industria, identificando momentos en los que el volumen total negociado supera significativamente su promedio histórico justo antes de un posible cambio de tendencia.

La lógica está inspirada en análisis técnico y flujo de capital institucional, aplicada de forma agregada por sector.

🧠 Idea principal

El Crossover de Volumen Industrial busca responder a esta pregunta:

¿Cuándo una industria completa empieza a mostrar un volumen anormalmente alto, anticipando un cambio de tendencia?

Para eso:

Se suma el volumen diario de todos los tickers de una misma industria.

Se compara contra su promedio histórico reciente.

Se detectan picos de volumen que suelen preceder movimientos relevantes en precios (ej. cruce de la SMA 50).

📈 Valor de negocio

Detecta acumulación institucional masiva

Permite anticipar rotaciones sectoriales

Útil para:

estrategias top-down

filtros previos a señales técnicas

análisis macro / sectorial cuantitativo

🗄️ Estructura de datos esperada

El script asume la existencia de las siguientes tablas:

precios_diarios
campo	descripción
ticker_id	Identificador del activo
fecha	Fecha de cotización
volume	Volumen negociado
tickers
campo	descripción
ticker_id	Identificador del activo
industria	Industria o sector
⚙️ Lógica de la consulta

Agrupa el volumen diario por industria y fecha

Calcula:

vol_total: volumen total diario de la industria

vol_hist: promedio histórico de volumen (ventana móvil)

Filtra casos donde:

el volumen actual es al menos el doble del promedio histórico

🔎 Interpretación de resultados

Señal fuerte: volumen industrial ≥ 2× su promedio reciente

Suele anticipar:

quiebres de medias móviles (ej. SMA 50)

cambios de régimen en el sector

No es una señal de entrada directa, sino un detector de contexto

🚀 Posibles extensiones

Integrar directamente el cruce de SMA 50

Normalizar volumen por capitalización

Ajustar ventana temporal dinámicamente

Visualizar resultados en dashboards (Power BI / Tableau / Python)

📝 Notas

La ventana de 20 días y el multiplicador ×2 son parámetros ajustables

Pensado para bases de datos con histórico diario consistente

Ideal como módulo dentro de un pipeline cuantitativo más grande
