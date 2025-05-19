API de Cursos Online - Spring Boot + SQL y NoSQL

Este proyecto es una API REST desarrollada con Spring Boot para la gestión de cursos online. Incluye integración con base de datos relacional (MySQL) y NoSQL (MongoDB).  

Tecnologías Utilizadas

- Java 17
- Spring Boot
- Spring Data JPA (SQL)
- Spring Data MongoDB (NoSQL)
- Lombok
- MySQL
- MongoDB (Compass)
- Maven
- Insomnia (para pruebas)

---


Cómo ejecutar el proyecto

1.Descarga y descomprime el proyecto

2. Configura las bases de datos
Relacional (SQL - MySQL)
Crea una base de datos llamada cursosdb.

Ejecuta el siguiente script SQL para crear las tablas:

-- Crear la base de datos (opcional, si aún no existe)
CREATE DATABASE IF NOT EXISTS sistema_cursos;
USE sistema_cursos;

-- Tabla: usuarios
CREATE TABLE usuarios (
    usuario_id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    tipo VARCHAR(20) NOT NULL
);

-- Tabla: cursos
CREATE TABLE cursos (
    curso_id INT AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(200) NOT NULL,
    descripcion TEXT,
    precio DECIMAL(10, 2) NOT NULL,
    categoria VARCHAR(100)
);

-- Tabla: inscripciones
CREATE TABLE inscripciones (
    inscripcion_id INT AUTO_INCREMENT PRIMARY KEY,
    usuario_id INT NOT NULL,
    curso_id INT NOT NULL,
    fecha_inscripcion DATE NOT NULL,
    estado VARCHAR(50),
    progreso INT DEFAULT 0,
    FOREIGN KEY (usuario_id) REFERENCES usuarios(usuario_id)
        ON DELETE CASCADE,
    FOREIGN KEY (curso_id) REFERENCES cursos(curso_id)
        ON DELETE CASCADE
);
![image](https://github.com/user-attachments/assets/d50e920a-2af9-46c9-b39e-197908191ce8)


Configura application.properties para conectar con tu base relacional:

Modifica la url y su contraseña
![image](https://github.com/user-attachments/assets/65661599-a782-4f03-bb77-fe5231384380)


NoSQL (MongoDB)
Asegúrate de tener MongoDB instalado y corriendo (puedes usar Compass).

Y crea las colecciones
 ![image](https://github.com/user-attachments/assets/365b6865-ad46-48cf-9fb2-984cab498c77)


Configura la conexión en application.properties (recuerda tener creada la bd):
![image](https://github.com/user-attachments/assets/5575015a-3ca3-483e-a84a-e1a72ea1be0d)



 Endpoints disponibles
Relacional (SQL)
GET /inscripciones → Listar inscripciones
![image](https://github.com/user-attachments/assets/78bc1972-8d97-4085-b2e8-fbe94d2b1b06)

GET /inscripciones/{id} → Obtener una inscripción
![image](https://github.com/user-attachments/assets/bc240a2f-de34-4718-8d26-9b52b64e7299)


POST /inscripciones → Crear inscripción
![image](https://github.com/user-attachments/assets/c2ad2fa2-0cbb-4dc7-8a17-c1b8728a8431)


PUT /inscripciones → Actualizar inscripción
![image](https://github.com/user-attachments/assets/9bac6d54-c579-410c-8f32-ae8a45fb7bf1)


DELETE /inscripciones/{id} → Eliminar inscripción
![image](https://github.com/user-attachments/assets/c80d36c6-7273-40c7-9276-30bca98d6ee8)


NoSQL (MongoDB)
GET /mongo/inscripciones → Listar inscripciones (MongoDB)
![image](https://github.com/user-attachments/assets/8aa3a580-d37f-4d75-8a1c-7b2974d7f2b6)


GET /mongo/inscripciones/{id} → Obtener una inscripción
![image](https://github.com/user-attachments/assets/416246de-3d68-4810-910b-a24e96313f94)


POST /mongo/inscripciones → Crear inscripción
![image](https://github.com/user-attachments/assets/8dddf3ce-c90d-413d-aa55-01d020a46eb8)


PUT /mongo/inscripciones → Actualizar inscripción
![image](https://github.com/user-attachments/assets/fab85844-d3ba-4ac8-aae7-1aeaefe555b0)


DELETE /mongo/inscripciones/{id} → Eliminar inscripción
![image](https://github.com/user-attachments/assets/974a2760-5b78-409f-83d5-3618022ecbff)

Uso de insomnia para pruebas HTTP


![image](https://github.com/user-attachments/assets/97a77aff-28f6-4032-acc5-58952d4373ac)

Estructura del Proyecto

![image](https://github.com/user-attachments/assets/0de931df-4aa0-4a16-96bd-e7ef300b1d12)

#Visualización de Datos con Power BI

Abre Power BI Desktop.

Selecciona Obtener datos > Web.

Ingresa la URL de la API:

Para inscripciones SQL: http://localhost:8080/inscripciones

Para inscripciones MongoDB: http://localhost:8080/mongo/inscripciones

Navega por el JSON recibido y selecciona la lista de inscripciones.

Carga los datos y repite el proceso para la otra API si quieres comparar.

![image](https://github.com/user-attachments/assets/d7bea461-9112-4e70-9f88-a0ac069fb8c4)

![image](https://github.com/user-attachments/assets/9044ec3a-f494-4701-a291-ead213225445)




