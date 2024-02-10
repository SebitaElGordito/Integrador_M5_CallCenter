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

<br>

Además, este Dashboard también puede ser una herramienta valiosa para el banco y sus clientes. Al ofrecer niveles de SLA a terceros, el banco puede garantizar un cierto nivel de servicio y calidad a sus clientes. Asimismo, al desarrollar un nuevo servicio Premium para los clientes más importantes del banco, el banco puede mejorar su relación con estos clientes y aumentar su satisfacción.
Por lo tanto, el proceso de EDA y ETL no sólo nos permite entender mejor los datos del Call Center, sino que también nos permite usar estos datos para mejorar la eficiencia, la productividad y la calidad del servicio del Call Center, y para proporcionar una herramienta valiosa para la gestión y la toma de decisiones en el Call Center.

<p align="center">
<img src="https://github.com/SebitaElGordito/Integrador_M4/blob/main/Imagenes_proyecto/Creacion_imagen_ubuntu.png" alt="imagen de creación de espacio en disco y montado de imagen ubuntu." width="650" height="420">
</p>

*Luego de colocarle nombre a la maquina virtual, se selecciona la pestaña de disco duro, y se selecciona la opción de Usar un archivo de disco duro virtual existente. En la ventana que se abre a continuación, se selecciona añadir, y se busca la imagen de linux ubuntu previamente descargada.*

<br>
<br>
<p align="center">
<img src="https://github.com/SebitaElGordito/Integrador_M4/blob/main/Imagenes_proyecto/Configuracion_servidor.png" alt="imagen de la configuración del servidor de la máquina virtual" width="650" height="420">
</p>

*Luego de haber montado la imagen del sistema operativo, se procede a la configuración del servidor. Ésta configuración radica en la cantidad de núcleos del procesador que se le asignará a la máquina virtual, asi como tambien la cantidad de GB de memoria RAM y se habilitarán los permisos y conexiones de red correspondientes para poder trabajar con el entorno local de windows.*

<br>
<br>
<p align="center">
<img src="https://github.com/SebitaElGordito/Integrador_M4/blob/main/Imagenes_proyecto/Conexion_putty.png" alt="imagen de conexión de máquina virtual con putty" width="650" height="420">
</p>

*Luego de haber configurado todo, se enciende la máquina virtual. Luego de que carguen todos los archivos y dependencias, se ingresa usuario y contraseña Ubuntu, y se ingresa el comando hostname -I para obtener la dirección IP del entorno local. Con ésta dirección IP se procede a conectar Putty, que lo que nos permite es una mayor libertad y mejor interacción con lo que estemos haciendo en el mismo entorno virtual.*

<br>



#### Limpieza del disco duro

Borrar todo: 

```
  docker system prune -a
```

#### Limpiar Carpetas

Visualizar las carpetas:

```
  ls
```
 
#### Eliminar carpetas (una por una):

```
  rm -r <Nombre de carpeta> 
```

#### Limpiar Contenedores

Visualizar contenedores:

```
    sudo docker ps
```

Eliminar TODOS los contenedores:

```
  sudo docker rm -f $(sudo docker ps -a -q)
```

#### Limpiar Volumen

Visualizar volumen:

    sudo docker volume ls

Eliminar TODO los volumenes:

```
  sudo docker volume prune
```

#### Limpiar Imágenes

Visualizar Imágenes:

```
  sudo docker image ls
```

Eliminar TODAS las imagenes:

```
  sudo docker image prune
```

#### Verificar si está limpio maquina virtual (MV)

Visualizar espacio disponible:

```
  df -h
```

<br>

## :calling: Clonación del repositorio, inicio y ejecución de los servicios docker-compose.yml

Para empezar, clonamos el repositorio, entramos dentro de la carpeta, e iniciamos, y ejecutamos los servicios dentro de docker-compose.yml, según el siguiente código...
```
  git clone https://github.com/lopezdar222/herramientas_big_data
  cd herramientas_big_data
  sudo docker-compose -f docker-compose-v1.yml up -d 
```

<br>

<p align="center">
<img src="https://github.com/SebitaElGordito/Integrador_M4/blob/main/Imagenes_proyecto/Clonando_repo.png" alt="imagen dentro de putty, clonación de repositorio de github" width="450" height="290">
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