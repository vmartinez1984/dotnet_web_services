# Arquitectura

El módulo esta nombrado como Arquitectura y Servicios Web, veremos algunas arquitecturas y patrones de diseño como:

Patron Repositorio

Unit of Work

Inyeccion de dependencias

Factory

Arquitectura n capas

# ¿Qué necesitamos?

Seguir dos reglas:

- Responsalididad única, una clase y/o método una tarea.
- Usar interfaces

De momento no nos preocupemos por saber que es un patrón o una aquitectura.

# Peliculas
Utilizaremos el ejemplo anterior, pero lo dividiremos y lo haremos complejo de manera inecesaria, pero será con fines didacticos, para ello debemos de generar biblioteca de clases:

- Pelicula.Presentaciones.Api
    - Controllers
    - Ayudantes

- Pelicula.Negocio
    - ReglasDeNegocio
    - Servicios        
    - Ayudantes

- Pelicula.Persistencia
    - Repositorios
    - Ayudantes
    - Contextos

- Pelicula.AlmacenDeArchivos
    - Almacen

- Pelicula.Persistencia.Core
    - Entidades
    - Interfaces

- Pelicula.Core
    - Dtos
    - Interfaces