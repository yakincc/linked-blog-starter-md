

# Introducción
El proyecto del Modelo Tipo Concierge fue desarrollado con la idea de proveer una forma de otorgar a los clientes del área de reparaciones de la compañía un puntaje que indique el nivel de prioridad de la atención, a partir de diversos factores, entre los cuales destacan la cantidad de , y buscar priorizar la atención de acuerdo con este puntaje. De acuerdo con el planteamiento del proyecto, la puntuación de prioridad del modelo de concierge se basa en 3 origenes distintos:

1. El grupo demográfico del cliente y su historial, que a partir de un modelo de segmentación desde los datos generales del cliente permita indicar qué tan probable es una reseña mala de acuerdo con sus características.
2. El vehículo del cliente, que a partir de un modelo de segmentación de las características del vehículo y de la póliza permita indicar qué tan probable es una reseña mala de acuerdo con sus características.
3. Los datos de la reparación del vehículo: El centro de Reparación al que se envía, la cantidad de piezas a reparar, el costo de refacciones, etc, 

A partir de esta información, se pretende realizar un modelo de regresión que permita calcular un puntaje de riesgo, para priorizar la atención de aquellos clientes de riesgo y evitar una mala reseña de su parte. 
