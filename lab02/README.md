# 📚 Tarea 1

## 🖥️ Tecnologías usadas 🖥️ 
 | Base de Datos | Entorno de Desarrollo |
 | ------------- | --------------------- |  
 | Mongo         | DataGrip              |
 

- ## Contenido ⌨️
    - [Creación de base de datos](#1-crear-base-de-datos)
    - [Creación de primera colección](#2-crear-primera-colección)
    - [Creación de segunda colección](#3-crear-segunda-colección)
    - [Visualización de colecciones](#4-mostrar-colecciones)
    - [Inserción de documentos](#5-crear-documentos)


## 1. Crear base de datos

```Js

    use TareaLab02

```


## 2. Crear primera colección

    

```Js

    db.createCollection('Estudiante')

```
## 3. Crear segunda colección

```Js

    db.createCollection('Carreras')

```
## 4. Mostrar colecciones

```Js

    show collections

```

## 5. Crear documentos

- ### Colección Estudiante    

```Js
    db.Estudiante.insertMany([
  { nombre: "Lucía", apellido: "Gómez", edad: 20, dni: "12345678" },
  { nombre: "Mateo", apellido: "Ramírez", edad: 22, dni: "23456789" },
  { nombre: "Valentina", apellido: "Fernández", edad: 21, dni: "34567890" },
  { nombre: "Santiago", apellido: "Pérez", edad: 23, dni: "45678901" },
  { nombre: "Camila", apellido: "Torres", edad: 19, dni: "56789012" },
  { nombre: "Joaquín", apellido: "López", edad: 24, dni: "67890123" },
  { nombre: "Martina", apellido: "Díaz", edad: 20, dni: "78901234" },
  { nombre: "Benjamín", apellido: "Ruiz", edad: 21, dni: "89012345" },
  { nombre: "Sofía", apellido: "Castro", edad: 22, dni: "90123456" },
  { nombre: "Tomás", apellido: "Morales", edad: 23, dni: "01234567" }]);


```

- ### Coleción Carrearas

```Js

    db.Carreras.insertMany([
  { _id: 1, nombre: "Ingeniería de Sistemas", departamento: "Tecnología", encargado: "Carlos Méndez" },
  { _id: 2, nombre: "Administración de Empresas", departamento: "Ciencias Económicas", encargado: "Laura Ríos" },
  { _id: 3, nombre: "Psicología", departamento: "Ciencias Humanas", encargado: "Martín Delgado" },
  { _id: 4, nombre: "Medicina", departamento: "Ciencias de la Salud", encargado: "Ana Rodríguez" },
  { _id: 5, nombre: "Arquitectura", departamento: "Diseño y Construcción", encargado: "Fernando Suárez" },
  { _id: 6, nombre: "Derecho", departamento: "Ciencias Jurídicas", encargado: "María Torres" },
  { _id: 7, nombre: "Contabilidad", departamento: "Ciencias Económicas", encargado: "Javier López" },
  { _id: 8, nombre: "Diseño Gráfico", departamento: "Arte y Diseño", encargado: "Lucía Vega" },
  { _id: 9, nombre: "Ingeniería Civil", departamento: "Ingeniería", encargado: "Héctor Paredes" },
  { _id: 10, nombre: "Educación Inicial", departamento: "Ciencias de la Educación", encargado: "Patricia León" }
]);

```
