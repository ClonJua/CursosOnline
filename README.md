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
![image](https://github.com/user-attachments/assets/edf747b3-36b9-4a79-9cae-cda1547fac91)

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


Configura application.properties para conectar con tu base relacional:

Modifica la url y su contraseña


NoSQL (MongoDB)
Asegúrate de tener MongoDB instalado y corriendo (puedes usar Compass).

Y crea las colecciones
 

Configura la conexión en application.properties:



 Endpoints disponibles
Relacional (SQL)
GET /inscripciones → Listar inscripciones


GET /inscripciones/{id} → Obtener una inscripción


POST /inscripciones → Crear inscripción


PUT /inscripciones → Actualizar inscripción


DELETE /inscripciones/{id} → Eliminar inscripción


NoSQL (MongoDB)
GET /mongo/inscripciones → Listar inscripciones (MongoDB)


GET /mongo/inscripciones/{id} → Obtener una inscripción


POST /mongo/inscripciones → Crear inscripción


PUT /mongo/inscripciones → Actualizar inscripción


DELETE /mongo/inscripciones/{id} → Eliminar inscripción

Uso de insomnia para pruebas HTTP

Estructura del Proyecto
src/
├── controller/
│   ├── InscripcionController.java
│   └── InscripcionMongoController.java
├── model/
│   ├── inscripcion/
│   │   ├── Inscripcion.java (SQL)
│   │   └── InscripcionMongo.java (MongoDB)
├── repository/
│   ├── InscripcionRepository.java
│   └── InscripcionMongoRepository.java
├── dto/
│   ├── RegistrarInscripcion.java
│   ├── ActualizarInscripcion.java
│   └── ObtenerInscripcion.java


