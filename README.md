# calculadoravue
Aplicación web SPA (Single Page Application) desarrollada con **Vue.js 3** y **Bootstrap 5 (vía CDN)** para el cálculo rápido y preciso del promedio ponderado de calificaciones de estudiantes.

## Enlace a la aplicación

Puedes acceder a la aplicación desplegada y en funcionamiento en el siguiente enlace:
**[https://juarez009.github.io/calculadoravue/](https://juarez009.github.io/calculadoravue/)**

## Como funciona
La aplicación permite registrar las notas obtenidas en los distintos períodos académicos con la siguiente ponderación:
* **Bloque 1:** 20%
* **Bloque 2:** 20%
* **Bloque 3:** 20%
* **Proyecto Final:** 40%
* **Total:** 100%

## Validaciones integradas en el SPA
* **Escala de calificación:** Valores válidos de **0 a 100**.
* **Gestión de campos vacíos:** Notifica al usuario si falta ingresar alguna de las calificaciones antes de operar.
* **Alertas visuales de Bootstrap 5:** Mensaje en rojo (`alert-danger`) ante errores de validación y resultado destacado en verde (`alert-success`) con la nota ponderada formateada a 2 decimales.

## Tecnologias utilizadas
* **Framework:** [Vue.js 3](https://vuejs.org/)
* **Estilos & Diseño Responsivo:** [Bootstrap 5.3](https://getbootstrap.com/) vía CDN
* **Despliegue & CI/CD:** GitHub Pages automatizado mediante GitHub Actions

## Comandos para el manejo del proyecto

### Para instalar dependencias del proyecto
```
npm install
```

### Para la ejecucion en local (desarrollo)
```
npm run serve
```

### Para la compilación del proyecto en produccion
```
npm run build
```