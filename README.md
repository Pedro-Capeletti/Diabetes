# 🩺 Base de Datos “Diabetes”
**📎 Enlace al Dataset**

https://www.kaggle.com/datasets/mohankrishnathalla/diabetes-health-indicators-dataset

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

** TABLA PRINCIPAL: Pacientes**
<img width="766" height="319" alt="image" src="https://github.com/user-attachments/assets/30a80644-52c3-42a4-837b-9d5a66be7a11" />

**TABLA Catálogo de Educación**
<img width="765" height="107" alt="image" src="https://github.com/user-attachments/assets/7acae166-c54f-437d-9ab3-e74d719ef817" />

**TABLA Catálogo de Etinias**
<img width="764" height="131" alt="image" src="https://github.com/user-attachments/assets/588020be-646c-4e97-a005-5ebab29e8eb8" />

**TABLA Catálogos de Ingresos**
<img width="766" height="107" alt="image" src="https://github.com/user-attachments/assets/b434a75d-24e5-4a75-9921-d8d0894731b1" />

**TABLA Ubicación Demográfica**
<img width="762" height="234" alt="image" src="https://github.com/user-attachments/assets/32ba5f3e-87b4-41c3-9bb4-572821095703" />

**TABLA Madiciones Físicas**
<img width="766" height="277" alt="image" src="https://github.com/user-attachments/assets/4e8267ac-52a8-433a-9714-fcc1b184469a" />

**TABLA Historial Médico**
<img width="761" height="226" alt="image" src="https://github.com/user-attachments/assets/8217d2cd-efc3-4539-b5d5-37ac7c7dd118" />

**TABLA Diagnóstico de Diabetes**
<img width="766" height="236" alt="image" src="https://github.com/user-attachments/assets/2b225fbb-3b0a-4258-b4e4-41b571579974" />

**TABLA Exámenes de Laboratorio**
<img width="764" height="255" alt="image" src="https://github.com/user-attachments/assets/01a6c07f-9f5f-40c7-83bb-42f1ac5ebe8e" />

**TABLA Hábitos de Vida**
<img width="761" height="250" alt="image" src="https://github.com/user-attachments/assets/f8bfa76d-3d1e-43c2-ad41-91357134bf73" />

**RELACIONES DE CATÁLOGO CON PACIENTES**
<img width="768" height="224" alt="image" src="https://github.com/user-attachments/assets/1aba40f2-dc75-415b-91e5-3b3fea24c26c" />



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
### 5️⃣ Consultas

**1. Mostrar la lista de los primeros 10 pacientes con su nombre completo y fecha de nacimiento.**

<img width="759" height="103" alt="image" src="https://github.com/user-attachments/assets/ab438b1d-06d5-4801-84b8-b8915ea38ee0" />


**2. Mostrar el promedio de IMC (BMI) de todos los pacientes.**

<img width="770" height="52" alt="image" src="https://github.com/user-attachments/assets/7301acb6-b69b-476d-b591-54f06fb5abf8" />


**3. Contar cuántos pacientes hay por género.**

<img width="767" height="83" alt="image" src="https://github.com/user-attachments/assets/d7b6ebc3-ebe9-4065-aced-eabb477d6d0c" />


**4. Obtener los pacientes diagnosticados con diabetes tipo 2.**

<img width="770" height="98" alt="image" src="https://github.com/user-attachments/assets/05e46163-bdb6-43fd-8b6c-b62fb34d206b" />


**5. Promedio de nivel de glucosa por tipo de diagnóstico.**
<img width="765" height="113" alt="image" src="https://github.com/user-attachments/assets/0c2687e9-befa-4466-9f95-629653f3e55f" />


**6. Ver los pacientes con presión arterial alta (>140/90)**

<img width="757" height="130" alt="image" src="https://github.com/user-attachments/assets/93c04945-2650-44b9-95ef-1423c96f7a66" />


**7. Identificar los pacientes que fuman y consumen alcohol semanalmente.**

<img width="773" height="124" alt="image" src="https://github.com/user-attachments/assets/d5b130d9-3635-4c19-9855-cbb13b3d653c" />


**8. Promedio de horas de sueño por género.**

<img width="769" height="131" alt="image" src="https://github.com/user-attachments/assets/573420a1-6093-4067-857b-5b7d450f21ad" />


**9. Mostrar el total de pacientes según su nivel educativo.**

<img width="767" height="135" alt="image" src="https://github.com/user-attachments/assets/fe06e0eb-726d-4cf1-81a0-519b6efee28c" />


**10. Identificar los pacientes con antecedentes familiares de diabetes.**

<img width="771" height="109" alt="image" src="https://github.com/user-attachments/assets/250f06f8-67b4-4c89-883a-2bb1eb0fe1d5" />


**11. Pacientes con colesterol > 200 y triglicéridos > 150.**

<img width="763" height="108" alt="image" src="https://github.com/user-attachments/assets/ec919a65-0f67-44d8-919e-df31eec96ac3" />


**12. Mostrar los pacientes, por provincia y ciudad.**

<img width="763" height="110" alt="image" src="https://github.com/user-attachments/assets/dc4b58bb-b538-46d5-a39a-09dc850b84e2" />

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


