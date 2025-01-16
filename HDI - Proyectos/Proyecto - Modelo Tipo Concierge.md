El proyecto del Modelo Tipo Concierge fue desarrollado con la idea de proveer una forma de otorgar a los clientes del área de reparaciones de la compañía un puntaje que indique el nivel de prioridad de la atención, a partir de diversos factores, y buscar priorizar la atención de acuerdo con este puntaje. De acuerdo con el planteamiento del proyecto, la puntuación de prioridad del modelo de concierge se basa en 3 origenes distintos:

1. El grupo demográfico del cliente y su historial, que a partir de un modelo de segmentación desde los datos generales del cliente permita indicar qué tan probable es una reseña mala de acuerdo con sus características, prediciendo el posible Net Promoter Score (NPS) de cada grupo demográfico.
2. El vehículo del cliente, que a partir de un modelo de segmentación de las características del vehículo y de la póliza permita indicar qué tan importante es ese cliente para la compañía, en términos monetarios.
3. Los datos de la reparación del vehículo: El centro de Reparación al que se envía, la cantidad de piezas a reparar, el costo de refacciones, etc, para determinar dado el vehículo y las características de la reparación, qué tan posible es recibir una mala crítica de su parte.

A partir de esta información, se pretende realizar un modelo de regresión que permita calcular un puntaje de prioridad, para priorizar la atención de aquellos clientes importantes y/o en riesgo de dar una mala reseña, con lo que efectivamente se pretende reducir la cantidad de encuestas con un NPS bajo, al tiempo que se asegura que los clientes de mayor importancia para la compañía dado su historial, permanezcan y recomienden a la compañía.

Hasta este momento, Se tiene ya el primer bosquejo de la segmentación de clientes para personas físicas con póliza individual a partir de sus características. En general, la información de mayor relevancia es extraída de las siguientes fuentes:

- ClienteUnico.TB_DWH_GrlPrimaVigentexOficinaAgente - Listado de información de Clientes Vigentes extraido desde Sybase. De aquí se extraen las siguientes características relevantes para el modelo:
	- Prima Neta Total
	- Edad
	- Antigüedad
	- Ocupación
	- Estado Civil

- expcliente.hdi_cucrudo en Snowflake - Obtiene la información de las primas pagadas en Auto o en Daños, y los totales de siniestros ocurridos en auto o en daños.
- TB_DWH_MedicionNPSAutos_Reparacion - Contiene la información del NPS de la empresa. Esta tabla es la tabla objetivo de la puntuación por cliente.
- DWH.Tb_BI_GrlSinReporte - Tiene el concentrado de reportes de siniestros ocurridos. 
- TB_BI_AutrFactEmisionDoc - Concentrado de documentos de emisión y cotizaciones.

Se tiene también un primer acercamiento a la segmentación por vehículos, aunque esta produce clusters mayormente influenciados por la marca y el modelo del vehículo. Tiene sentido, pero habría que hacer mayor trabajo al respecto. Así mismo, a día de hoy no tenemos forma de definir cuales vehículos tienen una póliza vigente o no.

Faltaría hacer la vinculación entre vehículos y reparaciones o valuaciones en general, para poder ver cómo afecta el tipo de vehículo y el centro de reparación en el NPS, y sobre esto, construir el modelo que asigne el puntaje de prioridad.







