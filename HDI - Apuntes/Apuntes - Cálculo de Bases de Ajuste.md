### Del proceso de Cálculo de Bases de Ajuste
1. Se obtienen los datos de los números de reporte de la oficina correspondiente a `NumOficina` y filtrada por ubicación geográfica (Límites de la oficina) desde una conexión por SQL a Procesos
2. Se realiza una detección y eliminación de outliers por coordenadas geográficas (Es decir, se eliminan los datos que no corresponden con la oficina).
3. Se obtiene una estimación de la cantidad óptima de clústeres siguiendo la metodología del codo de Jambu.
4. Se calcula la matriz de distancias de todos los puntos geográficos obtenidos.
5. Con el número de clústeres óptimos se realiza un agrupamiento de K-means para los datos geográficos de la oficina.
6. Los centros de los clústeres obtenidos son los que se definen como las bases de ajuste.
7. Se actualiza la tabla `CSL_Geolocalizacion_Centros_Gravedad` con las coordenadas de los centros de ajuste.

#### Mejoras propuestas: 
En lugar de utilizar el Codo de Jambu, se pueden buscar como alternativas:

| **Method**               | **Use Case**                                                       |
| ------------------------ | ------------------------------------------------------------------ |
| **Silhouette Score**     | For well-separated clusters and complex, non-spherical shapes.     |
| **Davies-Bouldin Index** | For clusters with varied densities and shapes.                     |
| **Gap Statistic**        | When data contains noise; good statistical robustness.             |
| **BIC/AIC**              | For Gaussian Mixture Models, when clusters may overlap.            |
| **DBSCAN/HDBSCAN**       | For irregular, non-spherical clusters, especially with noisy data. |
| **CH Index**             | Fast, compact, and well-separated clusters; simpler data.          |

Los algoritmos de clusterización buscan asignar todos los puntos a un grupo. Esto implica que pueden haber puntos muy alejados que "arrastran" el centro del grupo en el caso de K-Means. La eliminación de datos atípicos minimiza este error, pero si lo que se busca es encontrar puntos de máxima densidad de siniestros, se pueden utilizar modelos diferentes.

Flujo de trabajo sugerido:
- Realizar un análisis de densidad que muestre la tendencia de los datos espacialmente. Se puede usar para verificar que mes a mes la tendencia del agrupamiento espacial cambia. Sugerido: DBSCAN, Kernel Density Estimation, Gi* 
- Si la tendencia espacial es variable en el tiempo, entonces se puede automatizar su asignación usando una ventana de tiempo móvil para calcular datos de los centros dentro de un intervalo relevante. Si no se encontrara una variación significativa, entonces no es necesario calcular los centros de nuevo.
- Además, si se desea, se puede utilizar un modelo distinto para determinar la ubicación óptima de las bases, dependiendo de lo que más nos interese, incorporando métricas de tiempo de viaje o distancia de viaje en lugar de distancias euclidianas.