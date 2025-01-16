# Informe de Proyecto: Modelo Tipo Concierge

## 1. Resumen
El proyecto “Modelo Tipo Concierge” surge con la finalidad de asignar a los clientes del área de reparaciones de la compañía un puntaje que refleje el nivel de prioridad de atención. Este puntaje se basa en factores como las características demográficas del cliente, el tipo de vehículo y detalles de la reparación, con el objetivo de reducir las probabilidades de obtener un Net Promoter Score (NPS) bajo. 

Adicionalmente, se busca garantizar que aquellos clientes más importantes para la compañía, en términos de valor e historial, reciban un servicio prioritario y, con ello, se promueva su fidelidad y recomendación. Hasta el momento se cuenta con un primer bosquejo de segmentación para clientes con póliza individual, así como un acercamiento preliminar a la segmentación por vehículos.

---

## 2. Antecedentes
El área de reparaciones de la compañía recibe a diario numerosos clientes con necesidades y urgencias diversas. Sin embargo, no existe un mecanismo estandarizado para determinar cuál de estos clientes debería recibir una atención prioritaria basada en:
1. Su probabilidad de dejar una reseña negativa (impactando el NPS).
2. Su valor estratégico (en términos de póliza y relación a largo plazo).

Para solventar esta situación, se inició el desarrollo de un modelo de Concierge que asigna un puntaje de prioridad a cada cliente, considerando tres principales fuentes de información:
- **Perfil Demográfico e Historial del Cliente** (incluyendo probabilidad de reseña negativa a partir de su segmento y NPS potencial).
- **Características del Vehículo y de la Póliza** (importancia monetaria del cliente).
- **Datos de la Reparación** (centro, cantidad de piezas, costo de refacciones, etc.).

Este proyecto se encuentra en una fase preliminar, con un primer bosquejo de segmentación para personas físicas con póliza individual y un acercamiento inicial para la segmentación de vehículos.

---

## 3. Objetivos

### 3.1 Objetivo General
Desarrollar un modelo de regresión que calcule un puntaje de prioridad, para así priorizar la atención de clientes que presenten alto riesgo de emitir una reseña negativa y/o sean de gran valor para la compañía.

### 3.2 Objetivos Específicos
- Reducir la proporción de encuestas con NPS bajo.
- Identificar y fidelizar a los clientes más valiosos para la compañía.
- Integrar y consolidar datos de diferentes fuentes para la creación de un modelo robusto.
- Establecer un flujo de trabajo que aproveche el puntaje de prioridad en la operación diaria de reparaciones.

---

## 4. Alcance del Proyecto
El alcance del proyecto se limita a:
- Clientes con póliza individual en el ramo de automóviles.
- Datos relevantes de siniestros, pólizas, emisiones y NPS, según se encuentran registrados en las tablas y sistemas detallados en la sección de Metodología.
  
No contempla (por el momento):
- Integrar pólizas de otros ramos (salud, vida, etc.).
- Clientes con flotillas o personas morales.
- Analizar en profundidad los centros de reparación externos que no tengan registros en las fuentes de datos disponibles.

---

## 5. Metodología
Para la creación y entrenamiento del “Modelo Tipo Concierge”, se han de seguir los siguientes pasos:

1. **Recolección de Datos**  
   - **ClienteUnico.TB_DWH_GrlPrimaVigentexOficinaAgente (Sybase)**:  
     - Prima Neta Total  
     - Edad  
     - Antigüedad  
     - Ocupación  
     - Estado Civil  
   -  (Snowflake)**:  
     - Primas pagadas en Auto o Daños  
     - Totales de siniestros ocurridos en Auto o Daños  
   - **TB_DWH_MedicionNPSAutos_Reparacion**:  
     - Información del NPS de la compañía (tabla objetivo)  
   - **DWH.Tb_BI_GrlSinReporte**:  
     - Historial de reportes de siniestros  
   - **TB_BI_AutrFactEmisionDoc**:  
     - Información de documentos de emisión y cotizaciones  

2. **Segmentación del Cliente**  
   - Agrupar clientes de acuerdo con su probabilidad de reseña negativa (por medio de un posible NPS).  
   - Determinar importancia monetaria del cliente con un modelo de clusterización(basado en póliza, siniestros, valor asegurado, etc.).  

3. **Segmentación del Vehículo**  
   - Clasificación inicial basada en marca y modelo.  
   - Trabajo pendiente para determinar cuáles vehículos tienen póliza vigente.  

4. **Vinculación Vehículo-Reparaciones**  
   - Relacionar los datos de las reparaciones y valuaciones con los vehículos para analizar el impacto en el NPS.  

5. **Diseño e Implementación del Modelo de Regresión**  
   - Entrenamiento del modelo con la información consolidada.  
   - Validación y ajuste del puntaje de prioridad.  

---

## 6. Plan de Trabajo

| Etapa                                    | Descripción                                                                            | Responsable     | Estado      |
| ---------------------------------------- | -------------------------------------------------------------------------------------- | --------------- | ----------- |
| **1. Recolección de Datos**              | Recolectar datos de Data Warehouse, Snowflake y otras fuentes                          | Uriel Dominguez | En proceso  |
| **2. Segmentación de Clientes**          | Definir perfiles y clusters en función de NPS y valor                                  | Uriel Dominguez | Terminado   |
| **3. Segmentación de Vehículos**         | Definir perfiles y clusters en función del NPS y vehículo                              | -               | En proceso  |
| **4. Vinculación Vehículo-Reparaciones** | Integrar los registros de reparación y valuación con la información de vehículos y NPS | -               | Por Iniciar |
| **5. Diseño del Modelo de Regresión**    | Crear, entrenar y ajustar el modelo de puntaje de prioridad                            | -               | Por Iniciar |
| **6. Validación Piloto**                 | Realizar pruebas preliminares en un entorno controlado y obtener retroalimentación     | -               | Por Iniciar |
| **7. Implementación Final**              | Desplegar el modelo en entorno productivo, integrándolo con los visores pertinentes    | -               | Por Iniciar |


---

## 8. Análisis y Resultados (Estado Actual)
- Ya se cuenta con **un primer bosquejo de segmentación** para clientes personas físicas con póliza individual.  
- Se ha obtenido información relevante sobre **prima neta, edad, antigüedad, ocupación y estado civil**, que sientan las bases para estimar la probabilidad de recibir una reseña negativa o un NPS bajo.  
- En la **segmentación de vehículos**, se han identificado patrones de marca y modelo, aunque todavía es necesario profundizar para correlacionar el estado de la póliza y la vigencia de la cobertura, así como incluir los datos de las reparaciones en el modelo.

---

## 11. Próximos Pasos
- **Asegurar la integridad y disponibilidad de los datos**: Analizar el proceso manual de llenado de expcliente.hdi_cucrudo y llevarlo al Data Warehouse.
- **Completar la segmentación de vehículos**: Incluir la información de registro de reparaciones y vinculación con el NPS.  
- **Diseñar la fase de validación**: Probar el modelo de regresión y ajustar los parámetros según los resultados obtenidos.  
- **Desarrollar un plan de despliegue**: Definir cómo se integrará el puntaje de prioridad en el flujo de trabajo del área de reparaciones.  
- **Monitorear y mejorar**: Establecer indicadores clave (KPIs) para medir la eficacia del modelo y proponer mejoras continuas.  
