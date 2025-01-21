# Informe de Proyecto: Modelo Tipo Concierge

## 1. Resumen
El proyecto “Modelo Tipo Concierge” busca asignar a los clientes del área de servicio de la compañía un puntaje que indique el nivel de prioridad para su atención. Este puntaje considera factores como las características demográficas del cliente, el tipo de vehículo y datos de la reparación, con el fin de disminuir la probabilidad de obtener un Net Promoter Score (NPS) bajo.  

Además, se pretende que los clientes más importantes para la compañía, en términos de valor y trayectoria, reciban atención preferencial, fomentando así su permanencia y recomendación. A la fecha, se cuenta con un primer borrador de segmentación para clientes con póliza individual y un acercamiento preliminar para la segmentación de vehículos.

---

## 2. Antecedentes
El área de servicio de la compañía atiende diariamente a múltiples clientes con diversas necesidades y tiempos de respuesta. Sin embargo, no existe hasta el momento un proceso definido para determinar qué clientes debían ser atendidos con mayor prioridad basándose en:
1. Su probabilidad de dejar una reseña negativa (impactando el NPS).
2. Su valor estratégico (póliza, resolución del siniestro, historial y relación a largo plazo).

Para cubrir esta necesidad, se inició el desarrollo de un ***“Modelo Concierge”*** que, a partir de:

- **Perfil Demográfico e Historial del Cliente** (probabilidad de reseña negativa y potencial de NPS).
- **Características del Vehículo y la Póliza** (impacto monetario).
- **Datos de la Reparación** (centro de servicio, piezas a reparar, costos, etc.).

asigna un puntaje de prioridad a cada cliente. El proyecto se encuentra en fase inicial, con un primer esquema de segmentación para personas físicas con póliza individual y un estudio preliminar de vehículos.

---

## 3. Objetivos

### 3.1 Objetivo General
Desarrollar un modelo de regresión que calcule un puntaje de prioridad, enfocándose en clientes con mayor riesgo de emitir una reseña negativa y/o con alto valor para la compañía.

### 3.2 Objetivos Específicos
- Reducir la tasa de encuestas con NPS bajo.  
- Reconocer y fidelizar a los clientes más valiosos.  
- Consolidar fuentes de datos diversas para construir un modelo robusto.  
- Definir un proceso de atención que integre el puntaje de prioridad en la operación diaria.

---

## 4. Alcance del Proyecto
Este proyecto se limita a:
- Clientes con póliza individual en el ramo de autos residentes.
- Datos de siniestros, pólizas, emisiones y NPS, como se especifica en la sección de Metodología.

No considera actualmente:
- Otras líneas de negocio (Salud, Autos Turistas, etc.).
- Clientes con flotillas o personas morales.

---

## 5. Metodología
Para la creación y entrenamiento del “Modelo Tipo Concierge”, se deben seguir estos pasos:

1. **Recolección de Datos**: Desde la base de datos. Es quizás la parte más complicada y tardada del proyecto. Hasta el momento se tiene una buena recopilación de diversas fuentes de datos desde el Data Warehouse que proporcionan una fuente sólida de información de clientes vigentes y vehículos, pero la información referente a primas netas se encuentra en Snowflake y es alimentada por un proceso manual, que es necesario automatizar antes de tener mayor avance en el proyecto.

2. **Segmentación de Clientes**  
   - Estimar probabilidad de reseña negativa (posible NPS).  
   - Evaluar la importancia monetaria del cliente mediante modelos de clustering (póliza, siniestros, valor asegurado, etc.).  

3. **Segmentación de Vehículos**  
   - Clasificar vehículos por marca y modelo.  
   - Incorporar el estatus de póliza vigente (Pendiente).

4. **Vinculación Vehículo-Reparaciones**  
   - Integrar datos de reparaciones y valuaciones con la información de cada vehículo para medir el impacto en el NPS y poder predecirlo.  

5. **Diseño e Implementación del Modelo de Regresión**  
   - Entrenar el modelo con los datos consolidados.  
   - Validar y ajustar el puntaje de prioridad en función de resultados preliminares.

---

## 6. Plan de Trabajo

| Etapa                                    | Descripción                                                                         | Responsable     | Estado      |
| ---------------------------------------- | ----------------------------------------------------------------------------------- | --------------- | ----------- |
| **1. Recolección de Datos**              | Recolectar datos de Data Warehouse, Snowflake y otras fuentes                       | Uriel Domínguez | En proceso  |
| **2. Segmentación de Clientes**          | Definir perfiles y clusters en función de NPS y valor                               | Uriel Domínguez | Terminado   |
| **3. Segmentación de Vehículos**         | Definir perfiles y clusters con base en características del vehículo y NPS          | Por asignar     | En proceso  |
| **4. Vinculación Vehículo-Reparaciones** | Integrar registros de reparación y valuación con la información de vehículos y NPS  | Por asignar     | Por iniciar |
| **5. Diseño del Modelo de Regresión**    | Crear, entrenar y ajustar el modelo de puntaje de prioridad                         | Por asignar     | Por iniciar |
| **6. Validación Piloto**                 | Realizar pruebas preliminares con datos reales para obtener retroalimentación       | Por asignar     | Por iniciar |
| **7. Implementación Final**              | Desplegar el modelo en entorno productivo, integrándolo con los sistemas existentes | Por asignar     | Por iniciar |

---

## 7. Análisis y Resultados (Estado Actual)
- Existe un **primer bosquejo de segmentación** para clientes (personas físicas con póliza individual), que incorpora información relevante (prima neta, edad, antigüedad, ocupación, estado civil) para estimar la probabilidad de recibir una reseña negativa.  
- La **segmentación de vehículos** revela patrones por marca y modelo; aún se requiere enlazar pólizas vigentes y datos de reparaciones para valorar su efecto en el NPS.

---

## 8. Próximos Pasos
- **Asegurar la integridad y disponibilidad de los datos**: Llevar el flujo de información de CLTV de los clientes al Data Warehouse, dado que se encuentra como un proceso manual en Snowflake.
- **Completar la segmentación de vehículos**: Integrar la información de reparaciones y vincularla con el NPS.  
- **Diseñar la fase de validación**: Probar el modelo de regresión y ajustar parámetros según resultados iniciales.  
- **Definir un plan de despliegue**: Determinar cómo se integrará el puntaje de prioridad en el flujo de trabajo del área de reparaciones (Dashboards de Concierge).  
- **Monitorear y mejorar**: Establecer indicadores clave (KPIs) para evaluar la eficacia del modelo y proponer actualizaciones continuas.

---
