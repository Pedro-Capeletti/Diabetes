# Base de datos Diabetes
## Descripción
Conjunto de datos de indicadores de salud de la diabetes.

## Instalación
   1. Clone el siguiente repositorio.

   ```bash
git clone https://github.com/usuario/repositorio.git

   2. Cargar en su motor de base de datos el script o archivo SQL.

## Diagrama de Entidad - Relación
Este es el diagrama de Entidad Relación de la base de datos finalizado el proyecto:


## Explicación sobre como se realizo la normalización
  1. En primer lugar descargamos el archivo diabetes_dataset.csv, para poder ver como estabana organizado los datos y que tipo de separador se debia usar, para poder comenzar con la estructura de lo que va a ser la base de datos y sus tablas.
  
  2. Pasamos a crear la base de datos con la siguiente consulta.
     (INSERTAR IMAGEN)
     
  3. En este punto creamos las tablas que van a formar nuestra base de datos, definindo claves primarias  y foraneas y así creamos precisamente las tablas para cada archivo a importar.
     (INSERTAR TABLAS)
  
  4. En esta instancia comenzamos la carga de los datos con el siguiente comando y lo limitamos a 10.000 dado que el .csv tiene 100.000 datos.
  (INSERTAR IMAGEN)
  
  5. Una vez realizada la carga de datos en las tablas, empezamos a crear las consultas en el siguiente apartado.
     (CREATE VIEW vista AS SELECT...)

## Consultas
A continuación se muestran las consultas SQL que realizamos con la base de datos.
(INSERTAR CONSULTAS)


## Creador
Capeletti Pedro J. 
