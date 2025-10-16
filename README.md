# 🩺 Base de Datos “Diabetes”
**📎 Enlace al Dataset**

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


🖼️ -- 1️⃣ Listar los primeros 10 pacientes con su nombre completo y fecha de nacimiento
SELECT id_patient, CONCAT(first_name, ' ', last_name) AS nombre_completo, birth_date
FROM pacientes
ORDER BY birth_date DESC
LIMIT 10;

-- 2️⃣ Mostrar el promedio de IMC (BMI) de todos los pacientes
SELECT ROUND(AVG(bmi), 2) AS promedio_bmi
FROM mediciones_fisicas;

-- 3️⃣ Contar cuántos pacientes hay por género
SELECT gender, COUNT(*) AS cantidad
FROM pacientes
GROUP BY gender;

-- 4️⃣ Obtener los pacientes diagnosticados con diabetes tipo 2
SELECT p.id_patient, p.first_name, p.last_name, d.diagnosis_type, d.diagnosis_date
FROM diagnostico_diabetes d
JOIN pacientes p ON p.id_patient = d.patient_id
WHERE d.diagnosis_type LIKE '%tipo 2%';

-- 5️⃣ Promedio de nivel de glucosa por tipo de diagnóstico
SELECT d.diagnosis_type, ROUND(AVG(e.glucose_level), 2) AS promedio_glucosa
FROM diagnostico_diabetes d
JOIN examenes_laboratorio e ON e.patient_id = d.patient_id
GROUP BY d.diagnosis_type;

-- 6️⃣ Pacientes con presión arterial alta (>140/90)
SELECT p.first_name, p.last_name, m.blood_pressure
FROM mediciones_fisicas m
JOIN pacientes p ON p.id_patient = m.patient_id
WHERE CAST(SUBSTRING_INDEX(m.blood_pressure, '/', 1) AS UNSIGNED) > 140
   OR CAST(SUBSTRING_INDEX(m.blood_pressure, '/', -1) AS UNSIGNED) > 90;

-- 7️⃣ Pacientes que fuman y consumen alcohol semanalmente
SELECT p.first_name, p.last_name, h.smoking, h.alcohol
FROM habitos_vida h
JOIN pacientes p ON p.id_patient = h.patient_id
WHERE h.smoking IN ('Sí', 'smoker', '1')
  AND h.alcohol NOT LIKE '0%';

-- 8️⃣ Promedio de horas de sueño por género
SELECT p.gender, ROUND(AVG(h.sleep_hours), 2) AS promedio_sueño
FROM habitos_vida h
JOIN pacientes p ON p.id_patient = h.patient_id
GROUP BY p.gender;

-- 9️⃣ Número de pacientes por nivel educativo
SELECT ce.education_level, COUNT(p.id_patient) AS cantidad_pacientes
FROM pacientes p
JOIN catalogo_educacion ce ON ce.id_education = p.education_id
GROUP BY ce.education_level
ORDER BY cantidad_pacientes DESC;

-- 🔟 Mostrar pacientes con antecedentes familiares de diabetes
SELECT p.first_name, p.last_name, h.family_history
FROM historial_medico h
JOIN pacientes p ON p.id_patient = h.patient_id
WHERE h.family_history LIKE '%diabetes%';

-- 11️⃣ Pacientes con colesterol > 200 y triglicéridos > 150
SELECT p.first_name, p.last_name, e.cholesterol_level, e.triglycerides_level
FROM examenes_laboratorio e
JOIN pacientes p ON p.id_patient = e.patient_id
WHERE e.cholesterol_level > 200 AND e.triglycerides_level > 150;

-- 12️⃣ Mostrar los pacientes, su provincia y ciudad
SELECT p.first_name, p.last_name, u.province, u.city
FROM pacientes p
JOIN ubicacion_demografica u ON u.id_location = p.location_id
ORDER BY u.province, u.city;

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


