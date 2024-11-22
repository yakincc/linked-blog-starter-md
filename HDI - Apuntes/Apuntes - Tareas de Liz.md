
## Tareas Diarias
### Entregas de Reparación
1. Abrir el Dashboard `Analiz > Torre de Control de Entregas de Reparación.pbix`
2. Actualizar el Dashboard
3. Guardar el Dashboard
4. Publicar en `DS-CLS-EndUser`
### Listado de Cerrados
1. Abrir MS Edge
2. Abrir la pestaña Power BI de Favoritos
3. Navegar a `Áreas de Trabajo > DS-CSL-EndUser > [CSL] Listado para seguimiento de siniestros`
4. Verificar que la fecha que aparece en la esquina inferior izquierda es la fecha del día hábil anterior. En dado caso de que no sea correcta, ejecutar el script: `Scripts Necesarios > NuevaVista_ListadoCerrados.sql` y exportar los datos de la consulta generada a un archivo Excel.
5. Pasar el cursor sobre la tabla. Clic en el menú `...` > Exportar Datos > Datos con Diseño Actual
6. Mover el archivo `.xlsx` descargado a `Descargas > Listado Cerrados > Listado Dashboard`
7. Renombrar el archivo a la fecha hábil anterior.
8. Abrir MS Teams > Proyecto Concierge
9. Enviar el archivo de Excel

### Proyecto de Rechazos
1. Abrir Power Automate
2. Ejecutar el flujo `Actualización Rechazos`

### Bitácora de Monitoreo
1. Abrir SQL Server
2. Abrir los scripts: `Analiz > BITÁCORAS > Bitácora Monitoreo > Plantillas`
3. En el archivo etiquetado como "Plantilla 1", seleccionar con el cursor cada uno de los pasos y hacer clic en `Execute`
4. Abrir el archivo `OneDrive - HDI > Bitácora de Monitoreo.xlsx`
 5. En la hoja `Form 1`, buscar y guardar el número de la fila del último registro
 6. En la hoja `Hoja 1`, seleccionar la última fila y arrastrarla hasta la fila anterior a la del último registro.
 7. Seleccionar toda la tabla de la `Hoja 1` y copiar `Ctrl + C`
 8. Cerrar el archivo `.xlsx`
 9. En el archivo etiquetado como "Plantilla 2", pegar la selección debajo de la sección comentada
 10. Agregar el statement `GO` al final del script y Ejecutar.
 11. Abrir el archivo `Analiz > BITÁCORAS > Bitácora Monitoreo > Bitácora de Monitoreo Primera Atención.pbix`
 12. Actualizar, Guardar y Publicar el Dashboard en `CLS - Test`

### Bitácora de Traslados
1. Abrir el archivo `Analiz > BITÁCORAS > Bitácora Traslados > Traslados[CSL][2024].pbix`
2. Actualizar, guardar y publicar el Dash en `CLS - TEST`

--- 
## Tareas del Viernes
### Actualización del Pronóstico de Siniestros
1. Abrir el archivo `Inteligencia Operativa > Pronósticos > DASH DE PRONÓSTICO X HORA.pbix`
2. Actualizar, Guardar y Publicar en el área de Trabajo `URIEL PRUEBAS`
3. Abrir el archivo `Inteligencia Operativa > Pronósticos > RENDIMIENTO DE PRONÓSTICO POR HORA.pbix`
4. Actualizar, Guardar y Publicar en el área de Trabajo `URIEL PRUEBAS`
5. Abrir el archivo `Inteligencia Operativa > Pronósticos > CSL - Pronóstico por hora.pbix`
6.  Actualizar, Guardar y Publicar en el área de Trabajo `CSL - Proyectos de equipos de inteligencia operativa`
7. Abrir el archivo `Inteligencia Operativa > Pronósticos > CSL - Rendimiento por hora.pbix`
6.  Actualizar, Guardar y Publicar en el área de Trabajo `CSL - Proyectos de equipos de inteligencia operativa`

### Actualización del Pronóstico de Siniestros por Hora
1. Abrir SQL server y realizar una conexión al servidor `data.hdi.com.mx`
2. Abrir la carpeta  `Pronóstico de Siniestros > FUNCIONAL 271023 `
3. Abrir los scripts de los pasos 1 - 5 en SQL Server o R Studio según corresponda.
4. Ejecutar el script del paso 1.
5. En el script del paso 2, cambiar la variable `fecha_de_pred` al día viernes actual.
6. Guardar el script, luego presionar `Ctrl + A` y `Ctrl + Enter` o Ejecutar.
7. En caso de que en el paso 2 se obtuviera un  error, buscar la oficina nueva y agregarla en el paso 1 para omitirla.
8. Ejecutar el script del paso 3.
9. Ejecutar el script del paso 4.
10. Ejecutar el script del paso 5.

11. Abrir el archivo `Pronóstico de Siniestros > FUNCIONAL > BD_Time_Series.xlsx`
12. Abrir el resultado del paso 4, copiar todo y pegar en la hoja `Datos` de `BD_Time_Series.xlsx`
13. Abrir el resultado del paso 5, clic derecho en la esquina superior izquierda de la vista resultante y presionar `select all > copy with headers`. Pegar en la hoja `Pronóstico Semanal` con pegado especial y caracteres Unicode.
14. Verificar que ambas tablas de Excel tengan la misma cantidad de datos que las vistas.
15. Cerrar el archivo `BD_Time_Series.xlsx`

16. Abrir el archivo `CSL - Prosin - Wall - Mes.pbix`
17. Actualizar, Guardar y publicar el Dashboard en el área de trabajo `DS-CSL-APP`  

18. Abrir el archivo `Proyección Siniestros`
19.  Actualizar, Guardar y publicar el Dashboard en el área de trabajo `CLS - Proyectos del Equipo de Inteligencia Operativa (TEST)`

20. Abrir `Analiz > Proyección de Regionales`
21. Renombrar Pronóstico por Oficina al día anterior al viernes actual y Abrir.
22. En la Hoja de Pronóstico, Buscar la Columna Q, colocar el cursor en el primer valor de esa columna (No encabezado) y seleccionar todo hasta el final de la columna. Copiar y pegar como valores en la columna U.

23. Abrir el query del paso 4, clic derecho en la esquina superior izquierda de la vista resultante y presionar `select all > copy with headers`. En la hoja `Datos`, posicionarse en la primera casilla y pegar con pegado especial y texto Unicode.
24. Verificar nuevamente que la cantidad de filas corresponda con la cantidad de filas de la vista.

25. Abrir la hoja `Proyección`.
26. Ir a la columna AO, abrir el filtro y retirar el check de las primeras 7 fechas.
27. En la misma columna, agregar las siguientes 7 fechas del filtro. 
28. Ir a la columna CY, abrir el filtro, quitar todos los check y agregar los siguientes 7 checks
29. En la barra de herramientas, escoger la pestaña "Datos" y presionar "Actualizar Todo" 
30. En la hoja `Bajío`, verificar que las fechas correspondan con la semana actual. Si coincide, guardar y cerrar.

31. Crear carpeta de la fecha actual, copiar el archivo actualizado en dicha carpeta por duplicado.
32. A uno de los duplicados, retirar "Copia" y "v". Abrir este archivo.
33. Copiar toda la hoja de pronósticos y pegar como valores en la misma hoja.
34. Repetir en la hoja `Bajío` y el resto de zonas, salvo las hojas de `Proyección` y `Datos`. 
35. Eliminar las hojas de "Datos" y "Proyección"

36. Copiar y pegar el archivo modificado 6 veces. Renombrar cada uno con:
	- BAJÍO
	- CDMX
	- OCCIDENTE
	- NORTE
	- SUR
	- PRONÓSTICOS
37. Abrir cada archivo uno por uno y eliminar todas las hojas salvo las que se corresponden con el nombre del archivo.
38. Ocultar la hoja que no dice "Entregable" en cada uno de los archivos
39. Guardar (Dejar el cursor en la primera casilla)
40. Repetir para el resto de oficinas

41. Ir al correo > Enviados > Pronóstico de Oficinas > Responder a Todos.
42. Modificar la fecha y el texto, así como las fechas en la lista del correo para que coincida con el periodo escogido.
43. Tomar captura del dash de `Pronóstico de Siniestros`, copiar y pegar en el correo en tamaño pequeño.
44. Modificar las etiquetas del correo siguiendo la siguiente guía:
    - Muy Atinado: Valores del día y la predicción casi idénticos.
    - Atinado: Dentro de las dos líneas grises.
    - Desviado: Dentro de las dos líneas grises, pero cerca de los límites.
    - Muy desviado: Fuera de los límites.
45. Adjuntar los 6 archivos entregables
46. Enviar

---
## Tareas del Lunes
### Actualizar el Dashboard de Monitoreo General por Oficina
1. Abrir el archivo `Analiz > CSL - Monitoreo General por Oficina`
2. Actualizar, guardar y publicar en el área de trabajo `TEST`