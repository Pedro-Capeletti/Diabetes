# 🩺 Base de Datos “Diabetes”
📎 Enlace al Dataset

El conjunto de datos original utilizado puede encontrarse en el siguiente enlace:
(INSERTAR LINK AL DATASET AQUÍ)

---

## 📘 Descripción

Este proyecto fue desarrollado con el objetivo de **aprender y aplicar procesos de normalización de datos** provenientes de un archivo en formato **CSV**.

El conjunto de datos utilizado contiene **indicadores de salud relacionados con la diabetes**, incluyendo información sobre características demográficas, hábitos, antecedentes médicos y resultados de diagnóstico.

El trabajo se centró en:

- Analizar la estructura del dataset original.  
- Normalizar la información según las **formas normales** de diseño de base de datos.  
- Crear las tablas y relaciones en **MariaDB**.  
- Cargar los datos desde el archivo `.csv`.  
- Realizar consultas SQL para obtener información útil del conjunto de datos.

---

## 🧩 Diagrama Entidad–Relación (DER)

A continuación se presenta el **Diagrama de Entidad–Relación (DER)** que representa la estructura final de la base de datos una vez normalizada.

> 📸 *(INSERTAR IMAGEN DEL DIAGRAMA AQUÍ)*

El diagrama muestra las entidades principales, sus atributos y las relaciones entre ellas, asegurando **integridad referencial** y evitando **redundancia de datos**.

---

## ⚙️ Proceso de Normalización y Creación de la Base de Datos

### 1️⃣ Análisis inicial del dataset

Se descargó el archivo `diabetes_dataset.csv` y se examinó su estructura para:

- Identificar los nombres de las columnas.  
- Reconocer el tipo de datos de cada campo.  
- Determinar el separador utilizado (coma).  

Esto permitió planificar la estructura inicial de las tablas y definir las claves primarias y foráneas.

---

### 2️⃣ Creación de la base de datos

Se creó la base de datos principal con el siguiente comando SQL:

```sql
CREATE DATABASE diabetes;
USE diabetes;
```
(INSERTAR IMAGEN DEL SCRIPT DE CREACIÓN DE LA BASE DE DATOS)
---
### 3️⃣ Definición de tablas y relaciones

A partir del análisis de los datos, se diseñaron las tablas necesarias para representar correctamente las entidades y sus relaciones.

Cada tabla se definió con su clave primaria (PRIMARY KEY) y, en los casos necesarios, claves foráneas (FOREIGN KEY) para mantener la integridad referencial.

🖼️ (INSERTAR IMAGEN O CÓDIGO DE LAS TABLAS AQUÍ)
---
### 4️⃣ Carga de datos desde el archivo CSV

Una vez creadas las tablas, se procedió a la carga de los datos utilizando el comando:

LOAD DATA LOCAL INFILE 'ruta/diabetes_dataset.csv'
INTO TABLE nombre_tabla
FIELDS TERMINATED BY ','
LINES TERMINATED BY '\n'
IGNORE 1 ROWS;

**Para fines prácticos, la carga se limitó a 10.000 registros, dado que el archivo original contenía más de 100.000 filas.** 

🖼️ (INSERTAR IMAGEN DE LA CARGA DE DATOS)
---
### 5️⃣ Creación de vistas y consultas

Con la base de datos completa y funcional, se generaron vistas y consultas SQL para analizar los datos y obtener resultados significativos.

Ejemplo:

CREATE VIEW vista_pacientes_diagnostico AS
SELECT paciente_id, edad, glucosa, presion_sanguinea, resultado_diagnostico
FROM pacientes
WHERE resultado_diagnostico = 'Positivo';


🖼️ (INSERTAR IMAGEN O LISTADO DE CONSULTAS AQUÍ)
---
📊 Consultas SQL Realizadas

A continuación se incluyen algunas de las consultas desarrolladas en el proyecto:

(INSERTAR CONSULTAS Y SUS RESULTADOS O BREVE DESCRIPCIÓN)

Estas consultas permitieron realizar análisis exploratorios, filtrar pacientes según distintos criterios de riesgo y validar la consistencia de los datos cargados.

🧠 Resultados y Conclusiones

El proceso permitió comprender en profundidad la importancia de:

Diseñar una base de datos correctamente normalizada.

Garantizar la coherencia e integridad de los datos mediante claves foráneas.

Utilizar sentencias SQL para consultar y analizar información sanitaria de manera eficiente.
---

🗂️ Tecnologías utilizadas

**MariaDB 10.4.32**

**HeidiSQL** para la gestión y visualización de la base.

**CSV** original como fuente de datos.

**SQL** estándar para las sentencias y consultas.

***
👨‍💻 Autor
**Capeletti Pedro J.**


