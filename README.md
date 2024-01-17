![jd_matrix200](https://github.com/jadiazpe/Project_SiniestrosViales_CABA/raw/main/images/portada_seguridad_vial.jpg)
 [Por Jairo Díaz](https://www.linkedin.com/in/jairoadiaz/)

<br />

#
# ANÁLISIS DE DATOS SOBRE SINIESTROS VIALES EN LA CIUDAD AUTÓNOMA DE BUENOS AIRES (2016 - 2021)

### Información Contextual
Los siniestros viales son eventos que involucran vehículos en las vías públicas, los cuales pueden tener diversas causas como colisiones entre automóviles, motocicletas, bicicletas o peatones, atropellos, choques con objetos fijos, o incluso caídas de vehículos. Estos incidentes pueden tener consecuencias que van desde daños materiales hasta lesiones graves o fatales para los involucrados.

Las tasas de mortalidad relacionadas con siniestros viales son un indicador crítico de la seguridad vial en una región. Estas tasas se calculan, generalmente, como el número de muertes por cada cierto número de habitantes, o por cada cierta cantidad de vehículos registrados.

En Argentina, cada año mueren cerca de 4.000 personas en siniestros viales. Aunque muchas jurisdicciones han logrado disminuir la cantidad de accidentes de tránsito, estos sigue siendo la principal causa de muertes violentas en el país.


### El Proyecto
El Observatorio de Movilidad y Seguridad Vial (OMSV), del Gobierno de la Ciudad Autónoma de Buenos Aires, nos solicita la elaboración de un proyecto de "anális de datos", con el fin de generar información que le permita a las autoridades locales tomar medidas para disminuir la cantidad de víctimas fatales de los siniestros viales. Para tal fin, nos dejan a disposición un dataset que contiene información sobre los siniestros viales registrados en la Ciudad de Buenos Aires durante el periodo 2016-2021.


### Objectivos
1. Llevar a cabo un análisis básico de ETL
2. Desarrollar un análisis EDA robusto
3. Desarrollar un tablero de visualización (dashboard) que contenga los hallazgos, el desarrollo de los KPIs propuestos, así como la información que soporte los potenciales cursos de acción.
4. Llevar a cabo una presentación, de máximo 10 mins, con la información relevante del desarrollo del proyecto 

<br />

#
# ETAPAS DEL PROYECTO 
![steamstages](https://github.com/jadiazpe/Project_ML_Games/raw/main/src_img/Steamstages.png)
<br />

## I. Estudio EDA <br />
### I.1 Extraction, Transformation and Load (ETL) <br />

Fueron considerados tres (3) archivos, en formato excel, como fuentes primarias de información:
- [homicidios.xlsx](Notebooks/datasets/source)
- [comunas.xlsx](Notebooks/datasets/source)
- [pob_caba.xlsx](Notebooks/datasets/source)

Estos archivos fueron analizados con un ETL básico vía PowerBI, siendo entregados para trabajo de preparación de datos, dos (2) archivos CSV:
- [victimas.csv](Notebooks/datasets/ETL/victimas.csv)
- [hechos.csv](Notebooks/datasets/ETL/hechos.csv)

El trabajo de preparación se realizó en el notebook [assembler.ipynb](assembler.ipynb)


<br />
