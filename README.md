![portada_seguridad_vial.png](https://github.com/jadiazpe/Project_SiniestrosViales_CABA/raw/main/images/portada_seguridad_vial.jpg)
 [Por Jairo Díaz](https://www.linkedin.com/in/jairoadiaz/)

<br />

#
# ANÁLISIS DE DATOS SOBRE SINIESTROS VIALES EN LA CIUDAD AUTÓNOMA DE BUENOS AIRES (2016 - 2021)

### Información Contextual
Los siniestros viales son eventos que involucran vehículos en las vías públicas, los cuales pueden tener diversas causas como colisiones entre automóviles, motocicletas, bicicletas o peatones, atropellos, choques con objetos fijos, o incluso caídas de vehículos. Estos incidentes pueden tener consecuencias que van desde daños materiales hasta lesiones graves o fatales para los involucrados.

Las tasas de mortalidad relacionadas con siniestros viales son un indicador crítico de la seguridad vial en una región. Estas tasas se calculan, generalmente, como el número de muertes por cada cierto número de habitantes, o por cada cierta cantidad de vehículos registrados.

En Argentina, cada año mueren cerca de 4.000 personas en siniestros viales. Aunque muchas jurisdicciones han logrado disminuir la cantidad de accidentes de tránsito, estos sigue siendo la principal causa de muertes violentas en el país.


### El Proyecto
El Observatorio de Movilidad y Seguridad Vial (OMSV), del Gobierno de la Ciudad Autónoma de Buenos Aires, nos solicita la elaboración de un proyecto de "análisis de datos", con el fin de generar información que le permita a las autoridades locales tomar medidas para disminuir la cantidad de víctimas fatales de los siniestros viales. Para tal fin, nos dejan a disposición un dataset que contiene información sobre los siniestros viales registrados en la Ciudad de Buenos Aires durante el periodo 2016-2021.


### Objetivos
- A. Llevar a cabo un análisis básico de ETL

- B. Desarrollar un análisis EDA robusto

- C. Desarrollar un tablero de visualización (dashboard) que contenga los hallazgos, el desarrollo de los KPIs propuestos, así como la información que soporte los potenciales cursos de acción.
- D. Llevar a cabo una presentación, de máximo 10 mins, con la información relevante del desarrollo del proyecto 

---> KPIs propuestos:

Reducir en un 10% la tasa de homicidios en siniestros viales de los últimos seis meses, en CABA, en comparación con la tasa de homicidios en siniestros viales del semestre anterior.

Definimos a la tasa de homicidios en siniestros viales como el número de víctimas fatales en accidentes de tránsito por cada 100,000 habitantes en un área geográfica durante un período de tiempo específico. Su fórmula es: (Número de homicidios en siniestros viales / Población total) * 100,000.

Reducir en un 7% la cantidad de accidentes mortales de motociclistas en el último año, en CABA, respecto al año anterior.

Definimos a la cantidad de accidentes mortales de motociclistas en siniestros viales como el número absoluto de accidentes fatales en los que estuvieron involucradas víctimas que viajaban en moto en un determinado periodo temporal. Su fórmula para medir la evolución de los accidentes mortales con víctimas en moto es: (Número de accidentes mortales con víctimas en moto en el año anterior - Número de accidentes mortales con víctimas en moto en el año actual) / (Número de accidentes mortales con víctimas en moto en el año anterior) * 100. 

<br />

#
# ETAPAS DEL PROYECTO 
![proceso_sv.png](https://github.com/jadiazpe/Project_SiniestrosViales_CABA/raw/main/images/proceso_sv.png)

<br />

## I. ETL (Extraction, Transformation and Load) <br />

Fueron considerados tres (3) archivos, en formato excel, como fuentes primarias de información:
- [homicidios.xlsx](Notebooks/datasets/source)
- [comunas.xlsx](Notebooks/datasets/source)
- [pob_caba.xlsx](Notebooks/datasets/source)

Estos archivos fueron analizados con un ETL básico vía PowerBI, 
abriendo las tablas; HECHOS y VICTIMAS desde el archivo origen 'homicidios.xlxs', y se llevando a cabo un ejercicio simple de ETL:
	
**Tabla HECHOS:**
* Tratamiento de filas completas que solo contienen archivos 'Null'
* Ajuste del formato de las columnas 'HORA' y 'HH'
* Cambiar a tipo texto todas las columnas de la tabla
* Cambiar nombre de columnas a; 'LUGAR_HECHO', 'TIPO_CALLE', 'POSX', 'POSY', 'VH_ACUSADO'
* Pasar TRIM a todas las columnas texto de la tabla
* Pasar CLEAN a todas las columnas de la tabla
* Pasar UPPERCASE a todas la columnas de la tabla

**Tabla VICTIMAS:**
* Tratamiento de filas completas que solo contienen archivos 'Null'
* Cambiar a tipo texto todas las columnas de la tabla
* Cambiar nombre de columnas a; 'ID', 'FECHA_AA', 'FECHA_MM', 'FECHA_DD', 'ROL_VICTIMA', VH_VICTIMA, 'SEXO_VICTIMA', 'EDAD_VICTIMA', 'FECHA_DECESO'
* Pasar TRIM a todas las columnas de la tabla
* Pasar CLEAN a todas las columnas de la tabla
* Pasar UPPERCASE a todas la columnas de la tabla

Una vez finalizado este proceso fueron entregados para trabajo de preparación de datos, dos (2) archivos CSV:
- [victimas.csv](Notebooks/datasets/ETL/victimas.csv)
- [hechos.csv](Notebooks/datasets/ETL/hechos.csv)

Dicho trabajo de preparación y ensamblaje de la información, que permite continuar con el EDA, fue realizado en el notebook [assembler.ipynb](Notebooks/assembler.ipynb), el cual entregó como producto el archivo combinado (merged file); [victimas_hechos.csv](Notebooks/datasets/ETL/victimas_hechos.csv).

<br />

## II. EDA (Exploration Data Analysis) <br />

Este archivo combinado es utilizado para iniciar el estudio EDA, teniendo como `objetivo específico encontrar "correlaciones efectivas" entre las variables de interés para el estudio`.

El archivo elaborado para desarrollar el EDA fue [EDA.ipynb](Notebooks/EDA.ipynb), el cual muestra cinco (5) apartados de trabajo definidos:

**1. Visualización de Datos Geoespaciales** ---> visualizar en un mapa los siniestros viales registrados en los archivos fuentes.
 ![geoespacial.png](https://github.com/jadiazpe/Project_SiniestrosViales_CABA/raw/main/images/geoespacial.png)

**2. Ejercicio de filtración para aprovechamientode variables de interés**

**3. Tratamiento de Variables de interés**
* 3.1 Tratamiento de valores pérdidos | nulos | vacíos | duplicados


* 3.2 Tratamiento de valores atípicos (outliers)
    ![outliers.png](https://github.com/jadiazpe/Project_SiniestrosViales_CABA/raw/main/images/outliers.png)

    
* 3.3 Visualización de variables categóricas. Ver
    ![categoricas.png](https://github.com/jadiazpe/Project_SiniestrosViales_CABA/raw/main/images/categoricas.png)

* 3.4 Visualización Histográfica
    ![histograma.png](https://github.com/jadiazpe/Project_SiniestrosViales_CABA/raw/main/images/histograma.png)

* 3.5 Matriz de Correlaciones
    ![correlaciones.png](https://github.com/jadiazpe/Project_SiniestrosViales_CABA/raw/main/images/correlaciones.png)


**4. Conclusiones EDA - Correlaciones**

* **Sobre información inválida o pérdida (missing):**
Únicamente fueron encontrados errores simples en datos aislados de las variables de interés: 'HORA', 'HH', 'POSX' y 'POSY'. Todos superados sin incidencia alguna en el análisis EDA.

* **Sobre información de los datos atípicos (Outliers):**  
En las columnas; 'POSX' y 'POSY' fueron evidenciados datos atípicos, no obstante su existencia es explicable razonablemente. Para el tema de las localizaciones geoespaciales (POSX, POSY), los datos atípicos hacen relación al valor cero '0' que les fue asignado a aquellos campos en ausencia de algún valor en los datos del dataset original, representando apenas un 1.81% de la muestra para dichas variables.

* **Sobre la información de potenciales correlaciones entre las variables:**
Al respecto el ejercicio nos muestra evidencia de una fuerte relación, de '0.81' entre las variables; 'ROL_VICTIMA' y 'VH_VICTIMA', reflejando la importancia que tienen tanto el vehículo de movilización, como la posición que ocupa la víctima en dicho vehículo. Esas variables, a su vez parecen mostrar algunas correlaciones, aunque muy moderada, con las edades de las víctimas ('0.29' y '0.26' respectivamente). De igual forma, la variable 'FECHA_AA' (Año del siniestro) muestra una correlación de baja intensidad con la variable 'LUGAR_HECHO' ('0.28'), en tanto que la variable 'HH' (Hora del siniestro) tiene una relación moderada baja ('0.24') con el tipo de vehículo en el que se transporta la víctima siniestrada. Por último se evidencia una correlación baja, del '0.31' entre el lugar del siniestro (Dirección donde ocurrió el siniestro) y el tipo de vía de tránsito (Avenidas, Calles, Autopistas o Avenida General Paz).

<br />

## III. Elaboración de panel de instrumentos (dashboard)

* El archivo que controla el panel de instrumentos fue elaborado en Power BI, y puede ser bajado directament desde el siguiente vínculo:
[SiniestrosViales_dashboard.pbix](Dashboards/SiniestrosViales_dashboard.pbix)

![presentacion.png](https://github.com/jadiazpe/Project_SiniestrosViales_CABA/raw/main/images/presentacion.png)

<br />
<br />

## >>>


### Sobre los folders de este repositorio Github<br />

**[[/Dashboards]](Dashboards/):** Directorio que almacena los archivos Power BI.
<br />

**[[/Notebooks/datasets/ETL]](/Notebooks/datasets/ETL/):** Directorio que almacena los archivos CSV usados para los trabajos ETL, EDA y de alimentación de dashboards. 
<br />

**[[/Notebooks/datasets/source]](/Notebooks/datasets/source):** Directorio que almacena los archivos fuentes primarios que soportan el proyecto.
<br />

**[[/images]](/images):** Directorio que almacena todas las imágenes que ilustran la información del repositorio.<br />

