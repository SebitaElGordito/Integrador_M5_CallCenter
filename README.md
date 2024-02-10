# :bar_chart: Práctica Integradora M5 :bar_chart:

<br>


## :bank: Contexto "Anonymous Bank" Call-Center DataSet 

Este documento describe caso de negocio basado en un Call Center de un Banco: “Anonymous Bank” en Israel. El dataset contiene las llamadas registradas durante 12 meses (desde el 01/01/99 hasta el 31/12/99).

##### El call center de "Anonymous Bank" provee varios servicios diferentes:

* Información y transacciones sobre cheques y cuentas de ahorros, de sus clientes bancarios.
* Respuesta de voz generada por computadora con información sobre las cuentas de los clientes (a través del dispositivo VRU = Voice Response Unit (unidad de respuesta de voz). Una unidad de respuesta de voz (VRU) es un sistema de contestador telefónico automático que posee un hardware y software que permite a la persona que llama navegar a través de una serie de mensajes pregrabados y utilizar un menú de opciones mediante los botones de un teléfono o el reconocimiento de voz.)
* Brindar información a prospectos de clientes. 
* Soporte a los clientes del web-site de "Anonymous Bank" (clientes que acceden al Home Banking)

##### El call center esta conformado por:
* 8 posiciones de agentes para llamadas de clientes y prospectos
* 1 posición de supervisor
* 5 posiciones de agentes para llamadas para soporte de internet home banking (en un cuarto adjac room)


<br>

## :telephone_receiver: Call Center

Analizar las operaciones de un Call Center de un Banco, para proponer mejoras en:

* Eficiencia operativa, proponiendo mejoras operativas.
* Mejorar la satisfacción del cliente, cumpliendo los SLA comprometidos.
* Brindar una herramienta para la gestión y la toma de decisiones a los managers del Call Center.

En conclusión se solicita definir, construir y presentar un Dashboard que permita medir los niveles de calidad de servicio, eficiencia y productividad del Call Center.
Para ello, se propone que definamos los KPIs adecuados para poder medir los objetivos propuestos, y definir nuevos niveles objetivos de manera de ofrecer esos niveles de SLA a terceras partes, o generar un nuevo servicio Premium para los clientes mas importantes del banco.

<br>

## :stethoscope: EDA y ETL


Con el propósito es examinar en profundidad las operaciones del Call Center para identificar oportunidades de mejora en términos de eficiencia operativa y satisfacción del cliente, además de proporcionar una herramienta de gestión útil para los responsables del Call Center, se le realizó un EDA y ETL al Dataset provisto. El Análisis Exploratorio de Datos es una técnica que nos permite entender las características principales de nuestro conjunto de datos, generalmente a través de métodos visuales. En este caso, el EDA nos ayudará a descifrar los matices de los datos del Call Center, y a descubrir posibles áreas de mejora. Mientras que el ETL es un proceso que consiste en extraer datos de diferentes fuentes, transformarlos para satisfacer los objetivos comerciales y cargarlos en un sistema de destino.
A partir de este análisis, podremos definir los KPIs adecuados para medir los objetivos propuestos, y establecer nuevos niveles objetivos para ofrecer esos niveles de SLA a terceros, o para desarrollar un nuevo servicio Premium para los clientes más importantes del banco.

<br>

<p align="center">
<img src="https://github.com/SebitaElGordito/Integrador_M5_CallCenter/blob/main/Imagenes/EDA_ETL.png" alt="imagen de dataset en powerquery" width="650" height="370">
</p>

<br>

Se realizaron modificaciones en los valores de varias columnas , decidiendo no imputar esos datos, por encontrar una lógica para su transformación y conservación. En la columna de los agentes existian errores de ingreso de los nombres de los agentes. Estos datos podrían corroborarse pidiendo una lista de los nombres de los empleados, pero por ejemplo, se decidió unificar las llamadas asignadas al empleado NAAMAT con las del agente No_serverAMAT, o el empleado ANAT y los datos del empleado ANo_serverT, encontrando la relación lógica de que en los empleados donde existian las letras NA, por alguna razón se les modificaba a "No_server".
Se transformaron datos para una mejor comprensión, y se crearon columnas adecuadas que me permitiran la construcción de gráficos.
También se transformaron por ejemplo los datos en la columna de Tiempo de la Llamada en la Unidad de Respuesta de Voz, columna en la que figuraban valores negativos. Este error se debe a que el tiempo en URV se calcula restando la hora en la que se terminó la llamada con el URV y el tiempo de inicio de llamada con el URV. Si se invierten estos compos, por el motivo que sea, el resultado indefectiblemente será negativo, afectando de forma negativa tambien al tiempo en lista de espera, dado que para calcularse este tiempo se toma como "inicio de tiempo de espera" el valor que corresponde al final de la llamada con el URV, y si ese valor está alterado tambien lo estará el tiempo de espera. Se descontaron los segundos correspondientes al tiempo de espera en los casos en que el tiempo de llamada en URV eran negativos, aunque podrian haberse imputado esos datos, por tratarse del %0,009 en su conjunto, del total de los datos. 

<br>

## :bar_chart: Dashboard

Luego de que se aplicaron los procesos de EDA y ETL sobre el conjunto de datos provisto por el banco, nos encontramos en una posición donde podemos definir, construir y presentar un Dashboard que permita medir los niveles de calidad de servicio, eficiencia y productividad del Call Center.
Este Dashboard será una herramienta valiosa para los gerentes del Call Center, ya que proporcionará una visión clara y en tiempo real del rendimiento del Call Center. Los KPIs y los niveles objetivos que definamos a partir de nuestro análisis servirán como parámetros para evaluar la eficiencia y la productividad del Call Center, y para identificar áreas donde se puedan hacer mejoras.

<br>

<p align="center">
<img src="https://github.com/SebitaElGordito/Integrador_M5_CallCenter/blob/main/Imagenes/Dashboard.png" alt="imagen del dashboard creado en power bi" width="650" height="370">
</p>
<p align="center">
<i>Dashboard en Power Bi</i>
</p>

<br>

Además, este Dashboard también puede ser una herramienta valiosa para el banco y sus clientes. Al ofrecer niveles de SLA a terceros, el banco puede garantizar un cierto nivel de servicio y calidad a sus clientes. Asimismo, al desarrollar un nuevo servicio Premium para los clientes más importantes del banco, el banco puede mejorar su relación con estos clientes y aumentar su satisfacción.
Por lo tanto, el proceso de EDA y ETL no sólo nos permite entender mejor los datos del Call Center, sino que también nos permite usar estos datos para mejorar la eficiencia, la productividad y la calidad del servicio del Call Center, y para proporcionar una herramienta valiosa para la gestión y la toma de decisiones en el Call Center.


## :question: Preguntas

*  A) ¿Cuál es el nivel de servicio para los clientes Prioritarios? 
*  B) ¿Damos un mejor servicio que a los clientes normales?
*  C) ¿Qué volumen de llamadas atendemos? 
*  D) ¿Cuáles son los cuellos de botella? ¿En qué días? ¿En qué bandas horarias?
*  E) ¿Cómo es la eficiencia y productividad de nuestros agentes?
*  F) ¿Hay clientes recurrentes en el uso del servicio?
*  G) ¿Cuáles son los tipos de servicio más recurrentes?
*  H) ¿Podemos estimar la dotación necesaria para cumplir con una calidad de servicio determinada?  Ejemplo: si quiero que mi tiempo promedio de espera sea menor a 60 segundos?

<br>

### A) ¿Cuál es el nivel de servicio para los clientes Prioritarios?

Para responder cuál es el nivel de servicio para los clientes prioritarios, se deben establecer niveles de atención predefinidos, o tener cierta referencia para poder inferir que el servicio es bueno o malo. De otra manera, se hace dificil establecer exactamente un nivel de atención.
El nivel de servicio se refiere a la calidad y eficiencia con la que se atienden las necesidades y solicitudes de los clientes. Para los clientes prioritarios, esto puede implicar una atención más rápida, un acceso preferencial a servicios y recursos, y una mayor personalización en la atención al cliente. Teniendo en cuenta ésto ultimo, se puede decir que el servicio para clientes premium o de alta prioridad es mejor que el servicio a clientes normales.

<br>

<p align="center">
<img src="https://github.com/SebitaElGordito/Integrador_M5_CallCenter/blob/main/Imagenes/Clientes_prioritarios.png" alt="imagen de porción del dashboard mostrando kpi´s de clientes prioritarios" width="650" height="100">
</p>
<p align="center">
<i>KPI´s filtrados por clientes Premium
</i>
</p>

<br>

Al realizar el EDA, logré detectar que se podrían mejorar aun mas los indicadores para clientes premium. Por ejemplo, la dotación actual es de 8 posiciones de agentes para llamadas de clientes y prospectos, 1 posición de supervisor y 5 posiciones de agentes para llamadas para soporte de internet home banking (en un cuarto adjac room). La cantidad de llamadas mensuales es aproximadamente 4 veces menor de clientes que consultan por cuestiones de homebanking, respecto de llamadas de otro tipo, pero su TMG o Tiempo Medio de Gestión es 2 veces mayor. Teniendo en cuenta estas cuestiones, se podría designar a 1 de los 5 empleados en "posición para llamadas para soporte de internet home banking" para que en el caso de existir un llamada del tipo "Solicitud de llamada" y que la misma corresponda a un cliente premium, el empleado "de guardia" se comunique con el cliente premium y le preste servicio, para evitar uno de los problemas que existe en el call center, que es que al momento de ser llamados por el URV, el cliente es puesto en cola de espera, porque el Agente que se habia designado para tal fin, atendió otra llamada. Esto es viable si tenemos en cuenta que al año solo hay 4136 llamadas del tipo "solicitud de llamada" realizada por clientes premium, 345 llamados por mes, aproximadamente 12 llamados por día.

También se puede asignar al Agente "de guardia" a atender llamadas de clientes y prospectos, cuando no tiene "solicitudes de llamadas de clientes premium", lo que ayudaría a disminuir el tiempo medio de espera de los clientes premium, que actualmente se encuentra en 58 segundos.

<br>

### B) ¿Damos un mejor servicio que a los clientes normales?

En general, los clientes prioritarios suelen recibir un nivel de servicio más alto en comparación con otros clientes. Pero en este caso solo se aplica una disminución en su tiempo de espera (tiempo de espera x 1,5) haciendo que su tiempo de espera corra más rápido y adelantandose así en la cola.
Se podría mejorar aún más con atención personalizada definida en el punto A y seguimiento proactivo de las necesidades de los clientes prioritarios.

<br>

<p align="center">
<img src="https://github.com/SebitaElGordito/Integrador_M5_CallCenter/blob/main/Imagenes/Clientes_normales.png" alt="imagen de porción del dashboard mostrando kpi´s de clientes normales" width="650" height="100">
</p>
<p align="center">
<i>KPI´s filtrados por clientes Normales</i>
</p>

<br>

Teniendo en cuenta todo esto, y viendo las métricas, se concluye que el servicio NO es mejor para clientes premium, habiendo margen de mejora en varios aspectos.

<br>

### C) ¿Qué volumen de llamadas atendemos?

Atendemos un volumen de llamadas de 444.450 llamadas en total para el año 1999, lo que nos da un promedio de 37.000 llamadas por mes.

<br>

<p align="center">
<img src="https://github.com/SebitaElGordito/Integrador_M5_CallCenter/blob/main/Imagenes/Volumen_llamadas.png" alt="imagen de porción del dashboard mostrando volumen de llamadas por prioridad clientes" width="550" height="370">
</p>
<p align="center">
<i>Volumen de llamadas acumuladas, por mes, y por prioridades</i>
</p>

<br>
<br>

### D) ¿Cuáles son los cuellos de botella? ¿En qué días? ¿En qué bandas horarias?

Los cuellos de botella ocurren los dias domingo, a las 10 y a las 16. Indistintamente del día, la mayor cantidad de llamadas se registran en esos mismos horarios.

<br>

<p align="center">
<img src="https://github.com/SebitaElGordito/Integrador_M5_CallCenter/blob/main/Imagenes/Frecuencia_llamados.png" alt="imagen de Frecuencia de llamadas acumuladas por día (izquierda), y por hora (derecha) en los días con mayor número de llamadas." width="650" height="370">
</p>
<p align="center">
<i>Frecuencia de llamadas acumuladas por día (izquierda), y por hora (derecha) en los días con mayor número de llamadas. </i>
</p>

<br>
<br>

### E) ¿Cómo es la eficiencia y productividad de nuestros agentes?

La eficiencia es del 100% en la mayoría de los agentes, pero solo en llamadas asignadas vs llamadas atendidas, porque al no contar con un sistema de "encuesta de satisfacción", o algo parecido, desconocemos si los agentes fueron capaces de brindar un servicio y solucionar el motivo de consulta del cliente.
En la siguiente tabla se muestra los 10 empleados con mayor cantidad de llamadas atendidas, y algunos indicadores.

<br>

<p align="center">
<img src="https://github.com/SebitaElGordito/Integrador_M5_CallCenter/blob/main/Imagenes/eficiencia_empleados.png" alt="imagen de una tabla de empleados, mostrando métricas" width="650" height="420">
</p>
<p align="center">
<i>Tabla de TOP 10 de empleados con mayor volúmen de llamados anual, eficiencia, productividad y TMG.</i>
</p>

<br>
<br>

## Índice

* [Contexto](#contexto)

+ [Creación y conexión de la máquina virtual](#hammer-creación-y-conexión-de-la-máquina-virtual-entorno-linux)

  * [Limpieza de la máquina virtual (opcional)](#limpieza-de-la-máquina-virtual-opcional)

* [Clonación del Repositorio](#calling-clonación-del-repositorio-inicio-y-ejecución-de-los-servicios-docker-composeyml)

* [HDFS](#floppy_disk-hdfs---hadoop-distributed-file-system)

* [Hive](#bookmark_tabs-hive)

* [Formatos de Almacenamiento](#file_cabinet-formatos-de-almacenamiento)

* [SQL](#computer-sql)

+ [No-SQL](#card_file_box-no-sql)
  * [H-base](#h-base)

  * [Mondodb](#mongodb)

  * [Neo4j](#neo4j)

+ [Spark](#magic_wand-spark)

  * [Spark y Scala](#spark-y-scala)

  * [Kafka](#kafka)

  * [Comparativa Datasets y Dataframe en Scala](#comparativa-datasets-y-dataframe-en-scala)

* [Carga Incremental con Spark](#hourglass-carga-incremental-con-spark)

* [Herramientas de Orquestación de flujo de datos](#abacus-herramientas-de-orquestación-de-flujo-de-datos)

* [Participantes y compañeros del pair programming](#people_hugging-participantes-y-compañeros-del-pair-programming)