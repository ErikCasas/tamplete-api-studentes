# Planning

Planeación para la creación de API publica para los estudiantes de Ada School

> [!NOTE]
> Se utlizará el rol del estudiante implementado en el token generado por la plataforma de Ada para dar acceso a cada endpoint definido en esta API.

## Estructura

```javascript
{
"title": String
"description":String
"createdBy": IdStudent && ObjetcId
"dueDate": Date
"priority" Number
"isCompleted": Boolean
"data": Object
}
```

###### Se implementa la propiedad data para que el estudiante tenga la posibilidad de añadir nuevas propiedades como por ejemplo "Category"

###### Se implementa la propiedad createBy para poder responder con las tareas correspondientes a cada estudainte

### EndPoint

| verbo HTTP | end point                          | respuesta                                                     | Nota                                                                                                                    |
| ---------: | ---------------------------------- | ------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
|        GET | /api/v1/tasks                      | lista (array) de todas las tareas                             |                                                                                                                         |
|        GET | /api/v1/tasks/:taskId              | objeto tarea                                                  |                                                                                                                         |
|        GET | /api/v1/tasks?offset=Num&limit=Num | sección de la lista (array) de tareas                         | Con el fin de facilitar la creación de un paginado                                                              |
|        GET | /api/v1/tasks?completed=Boolean    | lista (array) de tareas filtrada por completas o no completas |                                                                                                                         |
|       POST | /api/v1/tasks                      | objeto nueva tarea                                            |                                                                                                                         |
|       POST | /api/v1/tasks/populate             | Mensaje base de datos llenada                                 | Con el fin de que el estudainante pueda volver a llenar la base de datos rapidamente despues de que esta se restablezca |
|        PUT | /api/v1/tasks                      | objeto tarea actualizada                                      |                                                                                                                         |
|     DELETE | /api/v1/tasks                      | objeto tarea eliminada                                        |                                                                                                                         |

---

### Lista de prioridades

#### Alta :warning:

- Definición del modelo para la tares (validar)
- Implementación de Autenticación y autorización
  - Esto en base al token que ya se genera en la plataforma de Ada school
- Implementación de CRUD basico
  - **C**REATE: ruta para la creación de una nueva tarea
  - **R**EAD: ruta para ver las tareas creadas por el estudiante en particular, en base al id del estudiante
  - **U**PDATE: ruta para actualizar una tarea en concreto
  - **D**ELETE: ruta para eliminar una tarea en concreto
- Funcionalidad de reinicio de datos cada 24h

#### Media :bangbang:

- Manejo de query strings para paginación en caso de tener un gran volumen de tareas
  - Esto se realiza en la ruta "GET" /api/v1/tasks
- Manejo de query string para filtrar las tareas por completas o no completas
  - Esto se realiza en la ruta "GET" /api/v1/tasks
- Creación de end point para población de datos facil en la base de datos
- Middlware para la validación de datos de entrada
- Manejo de errres

#### Baja :heavy_exclamation_mark:

- Optimización de rendimiento
- Soporte para archivos adjuntos
- Limitación en la cantidad de peticiones
- Limitación en la cantidad de datos
