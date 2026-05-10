Laboratorio 4 — VuelaAlpes · Script de video + Estructura Gamma

Instrucciones de grabación: Habla en un tono conversacional pero profesional. Las pausas indicadas con [pausa] son de ~1 segundo. Tiempo total estimado a ritmo normal: 2:50 – 3:00 min.

[0:00 – 0:20 · Introducción]

Hola, buenos días. Somos Zair Montoya y Tomás Hernández, del curso de Aprendizaje de Máquina. En este video les presentamos los resultados del Laboratorio 4, donde aplicamos técnicas de agrupación para ayudar a VuelaAlpes a entender mejor a sus pasajeros. [pausa]

[0:20 – 0:50 · El problema y los datos]

VuelaAlpes nos entregó un dataset con 10 000 registros de pasajeros. Cada registro incluye datos demográficos, características del vuelo y calificaciones de servicio. Nuestro objetivo era encontrar grupos de pasajeros con comportamientos similares, sin saber de antemano cuántos grupos existían ni cuáles eran. [pausa]

Para el modelado seleccionamos 10 variables numéricas: edad, distancia del vuelo y ocho calificaciones de servicio a bordo. Excluimos las variables categóricas para evitar expansión innecesaria del espacio, y descartamos los retrasos por sus distribuciones extremadamente asimétricas. Los datos se preprocesaron con un pipeline de imputación por mediana y escalamiento robusto.

[0:50 – 1:35 · Los tres algoritmos]

Evaluamos tres algoritmos con enfoques distintos. [pausa]

K-Means agrupa los datos minimizando la distancia de cada punto a su centroide. Usamos el método del codo y el análisis de Silhouette para determinar que k igual a 3 era el número óptimo de clusters.

Clustering Jerárquico Aglomerativo construye una jerarquía de fusiones de abajo hacia arriba. Usamos el dendrograma para confirmar que k igual a 3 tenía sentido, y el enlace ward como el mejor vínculo disponible.

DBSCAN identifica clusters como regiones de alta densidad. Sin embargo, en este dataset los pasajeros forman una distribución continua sin zonas densas diferenciadas, por lo que el algoritmo no encontró una estructura válida en ninguna configuración evaluada.

[1:35 – 2:05 · Evaluación y mejor modelo]

Comparamos los tres algoritmos con métricas intrínsecas: Silhouette, Davies-Bouldin y Calinski-Harabasz. [pausa]

K-Means obtuvo el mejor resultado en las tres métricas: Silhouette de 0.17, Davies-Bouldin de 1.97 y Calinski-Harabasz de 2 101. El Jerárquico quedó segundo con valores similares, y DBSCAN quedó descartado al no producir una agrupación válida. Por eso seleccionamos K-Means con k igual a 3 como el modelo final.

[2:05 – 2:45 · Interpretación de los grupos]

Los tres clusters tienen perfiles claramente distintos. [pausa]

El Cluster 0 agrupa 4 480 pasajeros: son pasajeros de mayor edad, vuelos más largos, y calificaciones muy altas en entretenimiento, comodidad y limpieza. Son el segmento que ya valora positivamente la experiencia a bordo.

El Cluster 1 agrupa 2 809 pasajeros más jóvenes, con vuelos cortos y las calificaciones más bajas en servicios de cabina. Es el segmento con mayor potencial de mejora en la experiencia en vuelo.

El Cluster 2 agrupa 2 711 pasajeros maduros con expectativas altas, pero con calificaciones bajas en servicio a bordo, espacio para las piernas y manejo de equipaje. Aquí el factor crítico es el servicio humano de la tripulación.

[2:45 – 3:00 · Cierre]

Estos tres perfiles le permiten a VuelaAlpes enfocar sus esfuerzos: innovar en servicios para pasajeros jóvenes, capacitar a la tripulación para pasajeros con altas expectativas, y mantener la propuesta premium para su segmento más satisfecho. Gracias.
