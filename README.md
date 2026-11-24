# The Twelve-Factor App

## ¿Qué es?

**The Twelve-Factor App** es una metodología con 12 principios para construir aplicaciones web y servicios SaaS que sean fáciles de desplegar, escalar y mantener en la nube. La propuso en 2011 **Adam Wiggins**, cofundador de **Heroku**, a partir de la experiencia de su equipo con miles de aplicaciones desplegadas en esa plataforma. Sirve como guía para crear aplicaciones portables, sin dependencia de un servidor específico, preparadas para contenedores y despliegue continuo, y que pueden crecer sin rediseñarse. 

### 1. Codebase: un repositorio, muchos despliegues

Cada aplicación vive en un único repositorio de GitHub, y de ese mismo código salen todos los despliegues: desarrollo, pruebas y producción. Los entornos no tienen copias distintas del código. Usan el mismo repositorio, organizado por ramas y flujos de trabajo, y cambian solo su configuración. Así tenemos una única fuente de verdad, trazabilidad de cada cambio y un trabajo en equipo más ordenado.

### 2. Config: configuración en variables de entorno

Las credenciales, URLs, claves y cualquier valor que cambie entre entornos no se escriben en el código. Se definen en variables de entorno: archivos `.env` excluidos del repositorio, *secrets* de GitHub o variables del contenedor en Docker. Esto protege la información sensible y permite construir aplicaciones y módulos parametrizables, que se pueden reutilizar después en otros proyectos sin tocar el código.

### 3. Concurrency: escalamiento horizontal

La aplicación crece agregando más procesos en paralelo, no haciendo más grande un solo servidor. Con Docker esto se hace levantando más contenedores de la misma imagen según la demanda. Por eso es clave diseñar servicios sin estado y desacoplados, capaces de atender más usuarios sin cambiar la arquitectura.

### 4. Dev/prod parity: paridad entre entornos

Desarrollo, pruebas y producción deben parecerse lo más posible en herramientas, dependencias y versiones. Docker lo hace posible porque la misma imagen corre igual en el equipo del desarrollador y en el servidor, lo que elimina el clásico "en mi máquina sí funciona". Con GitHub Actions se reduce además el tiempo entre escribir un cambio y publicarlo. Para el negocio esto significa menos errores en producción, entregas más rápidas y frecuentes, y más confianza en cada lanzamiento.