# ObraTech

**Plataforma web para conectar clientes, contratistas y trabajadores del sector de la construcción en Colombia.**

Repositorio académico del Proyecto de Aula. Este documento describe el propósito de ObraTech, su organización técnica y el componente complementario de minería de datos preparado para la asignatura **Minería de Datos I**.

> **Estado de la documentación:** la descripción funcional se basa en la estructura y documentación disponible en el repositorio. Los pasos de ejecución pueden variar según la configuración local del equipo; antes de ejecutar el sistema, revisa los archivos de configuración del backend y del frontend. No se deben publicar contraseñas, tokens ni credenciales.

## 1. Descripción general

ObraTech busca facilitar la conexión entre las personas y organizaciones que participan en proyectos de construcción. La plataforma contempla distintos perfiles de usuario y procesos relacionados con la publicación y gestión de proyectos, la búsqueda de oportunidades, las postulaciones, la administración de perfiles profesionales y la interacción entre clientes y contratistas.

En los procesos tradicionales de contratación pueden presentarse dificultades para encontrar personas calificadas, organizar las postulaciones y mantener información clara sobre el avance de los proyectos. ObraTech propone centralizar parte de esta interacción en una plataforma web, con el propósito de mejorar la organización, la trazabilidad y el acceso a la información relevante.

### Objetivo general

Desarrollar una plataforma web que apoye la publicación y gestión de proyectos, la conexión entre clientes, contratistas y trabajadores, y el seguimiento de la información asociada a la contratación dentro del sector de la construcción.

### Objetivos específicos

- Facilitar que los clientes publiquen y administren proyectos.
- Permitir que contratistas y trabajadores consulten oportunidades y participen en procesos de postulación, de acuerdo con su perfil.
- Organizar la información de los perfiles y la experiencia profesional.
- Apoyar la asignación de contratistas, la gestión de equipos y el seguimiento de proyectos.
- Proporcionar mecanismos de calificación y consulta de información para apoyar decisiones de contratación.
- Explorar el uso de minería de datos como componente académico complementario para comprender patrones en información contractual pública.

## 2. Roles y funcionalidades

Las funcionalidades disponibles dependen del estado actual del código y de la configuración del sistema. La documentación del repositorio identifica los siguientes roles y áreas funcionales:

| Rol | Funcionalidades documentadas |
|---|---|
| **Cliente** | Publicar y administrar proyectos, consultar postulantes, revisar proyectos en proceso, gestionar su perfil, consultar reportes y calificar contratistas. |
| **Contratista** | Gestionar su perfil, consultar proyectos asignados, revisar historial de proyectos y organizar equipos de trabajo. |
| **Trabajador** | Gestionar su perfil laboral, consultar proyectos disponibles, revisar y administrar sus postulaciones y consultar información del equipo. |
| **Administrador** | Consultar y administrar usuarios, revisar perfiles y apoyar tareas de gestión de la plataforma. |

Estas descripciones documentan áreas funcionales identificadas en el proyecto; no implican que todas las funciones estén desplegadas en un servidor público ni que hayan sido sometidas a pruebas de aceptación.

## 3. Arquitectura y tecnologías

El repositorio está organizado en un backend y un frontend independientes:

- **Backend:** aplicación Java basada en Spring Boot y administrada mediante Maven. Expone servicios REST para funciones como autenticación, perfiles, proyectos y calificaciones.
- **Frontend:** aplicación React organizada en la carpeta `frontend/`; la documentación de migración del proyecto describe el uso de Vite para el desarrollo del frontend.
- **Comunicación:** el frontend consume endpoints REST publicados por el backend.
- **Autenticación:** la documentación técnica registra un endpoint de inicio de sesión con JWT y flujos relacionados con OAuth2. Los mecanismos exactos deben verificarse en la configuración actual antes de desplegar.
- **Archivos y recursos:** el repositorio incluye una carpeta `uploads/` y recursos del frontend. Debe revisarse su contenido antes de publicar archivos que puedan contener datos personales.

### Estructura principal del repositorio

```text
Obratech/
├── backend/                         # Servicios y lógica del servidor
├── frontend/                        # Aplicación web React
├── uploads/                         # Archivos cargados por la aplicación
├── .mvn/wrapper/                    # Maven Wrapper
├── pom.xml                          # Configuración Maven del proyecto raíz
├── mvnw                             # Maven Wrapper para Linux/macOS
├── mvnw.cmd                         # Maven Wrapper para Windows
├── run.bat                          # Script de ejecución para Windows
├── obratech_react_migration_analysis.md
└── README.md                        # Documentación principal
```

El listado es una guía de las carpetas y archivos principales identificados en el repositorio; pueden existir otros archivos y subdirectorios dentro de `backend/` y `frontend/`.

## 4. Funcionalidades técnicas documentadas

La documentación de migración del proyecto registra, entre otros, los siguientes grupos de endpoints REST:

| Recurso | Operaciones documentadas | Propósito |
|---|---|---|
| Autenticación | `POST /api/auth/login` | Inicio de sesión. |
| Perfiles | `GET`, `POST`, `PUT` y `DELETE` bajo `/api/perfiles` | Consultar, crear, actualizar y eliminar perfiles. |
| Proyectos | `GET`, `POST`, `PUT` y `DELETE` bajo `/api/proyectos` | Consultar y gestionar proyectos. |
| Asignación | `POST /api/proyectos/{id}/asignar/{perfilId}` | Asociar un perfil con un proyecto. |
| Calificaciones | `GET /api/calificaciones`, `POST /api/calificaciones` | Consultar y registrar calificaciones. |

La lista es orientativa y se basa en la documentación del repositorio. Para confirmar los contratos completos de la API, validaciones, permisos y respuestas, consulta los controladores y servicios del backend.

## 5. Requisitos previos

Antes de ejecutar la aplicación, comprueba que el equipo tenga instaladas las versiones compatibles con los archivos del proyecto:

- Git.
- Java Development Kit (JDK), en la versión requerida por la configuración de Maven.
- Node.js y npm, compatibles con el proyecto React.
- El motor de base de datos configurado en los archivos del backend.

No se fijan versiones en este README porque deben coincidir con la configuración real del proyecto. Revisa `backend/pom.xml`, `frontend/package.json` y los archivos de configuración de Spring antes de instalar dependencias.

## 6. Ejecución en entorno local

### 6.1 Obtener el código

```bash
git clone https://github.com/juancitomiranda6-2005/Obratech.git
cd Obratech
```

### 6.2 Configurar el backend

1. Abre la carpeta `backend/` y revisa los archivos de configuración de Spring Boot.
2. Configura la conexión a la base de datos y las variables necesarias para autenticación u otros servicios.
3. Utiliza valores locales de desarrollo. No subas contraseñas, claves privadas, tokens ni datos reales de usuarios al repositorio.
4. Desde la raíz del proyecto, consulta `run.bat` si trabajas en Windows y verifica qué tareas ejecuta antes de utilizarlo.
5. Si necesitas iniciar el backend manualmente, entra a `backend/` y utiliza el Maven Wrapper con el objetivo de ejecución configurado para el proyecto. Por ejemplo, en proyectos Spring Boot suele utilizarse `./mvnw spring-boot:run` en Linux/macOS o `mvnw.cmd spring-boot:run` en Windows, siempre que la configuración del módulo lo permita.

### 6.3 Configurar el frontend

1. Abre una terminal dentro de `frontend/`.
2. Revisa `package.json` para confirmar los scripts disponibles y las versiones requeridas.
3. Instala las dependencias con `npm install`.
4. Ejecuta el script de desarrollo definido en `package.json`, habitualmente `npm run dev` en proyectos Vite.
5. Comprueba que la URL base de la API configurada en el frontend coincida con la dirección y el puerto del backend.

Los comandos anteriores son una guía de arranque para un entorno local. Si aparece un error, verifica primero las versiones de Java y Node.js, la configuración de base de datos, los puertos y las variables de entorno.

## 7. Componente académico de minería de datos

Como actividad complementaria de **Minería de Datos I**, se preparó un análisis inicial de datos públicos de contratación del portal Datos Abiertos de Colombia. Este análisis no reemplaza las funcionalidades del prototipo web: constituye un experimento académico independiente que explora si la información contractual pública permite estudiar patrones útiles para la toma de decisiones.

### Fuente de datos

- **Conjunto de datos:** CCE SECOP II.
- **Portal oficial:** [Datos Abiertos de Colombia](https://www.datos.gov.co/Gastos-Gubernamentales/CCE-secop-ii/tjbh-5nnb).
- **Archivo utilizado durante el análisis:** una muestra CSV con 4.400 filas y 67 columnas.

La muestra analizada corresponde a registros asociados con Bogotá y el sector Planeación. Por tanto, no debe considerarse representativa de todas las obras de construcción de Colombia ni de todos los usuarios potenciales de ObraTech.

### Pregunta de análisis

¿Qué características de los registros contractuales se relacionan con el estado reportado del contrato?

### Enfoque experimental

Se preparó un flujo de clasificación supervisada que utiliza el campo de estado contractual como variable objetivo y características contractuales disponibles como variables predictoras. El código emplea preparación de variables categóricas y numéricas, separación de entrenamiento y prueba, un clasificador Random Forest y una comparación con un clasificador de referencia.

**Alcance y limitaciones:** el experimento clasifica estados administrativos del contrato; no predice directamente retrasos de obras, calidad del contratista, incumplimiento futuro ni éxito de proyectos de ObraTech. Antes de utilizarlo como funcionalidad real de la plataforma, se necesita evaluar una fuente de datos más específica y validar la utilidad del modelo para una decisión concreta.

### Archivos del análisis

```text
mineria-datos/
├── analisis_obratech.py
├── analisis_obratech.ipynb
└── resultados/
    ├── distribucion_estados.png
    └── matriz_confusion.png

data/
└── README.md                      # Instrucciones para obtener el CSV
```

El CSV original no se incluye en el repositorio complementario. Descárgalo de la fuente oficial y guárdalo como `data/CCE_secop_ii.csv`, respetando las condiciones de uso y evitando publicar información personal innecesaria.

### Ejecutar el análisis

Desde la raíz del repositorio que contiene la carpeta `mineria-datos/`:

```bash
pip install pandas scikit-learn matplotlib jupyter
python mineria-datos/analisis_obratech.py
```

Para abrir el notebook:

```bash
jupyter notebook mineria-datos/analisis_obratech.ipynb
```

Los resultados pueden variar si cambia el archivo de entrada, sus columnas, el filtrado o las versiones de las librerías. Los valores numéricos deben citarse como resultados del experimento concreto que se ejecutó, no como una garantía de rendimiento futuro.

## 8. Entregables de Minería de Datos I

La guía de la asignatura solicita tres productos relacionados entre sí:

1. **Repositorio del prototipo:** código de ObraTech, análisis, scripts, notebook, evidencias y documentación.
2. **Propuesta del modelo predictivo:** definición del problema, fuente de datos, variables, técnica propuesta y estrategia de evaluación.
3. **Informe metodológico:** descripción del procedimiento realizado, decisiones de preparación, modelo, resultados comprobados y limitaciones.

Los documentos generados para la actividad pueden organizarse en `documentos/` y los archivos de análisis en `mineria-datos/`. Las capturas de MinedApp deben añadirse después de realizar el procedimiento en esa herramienta; no se deben simular evidencias que no se hayan obtenido.

## 9. Privacidad, seguridad y uso responsable

- No subas contraseñas, tokens, claves privadas, archivos `.env` con secretos ni credenciales de bases de datos.
- Revisa la carpeta `uploads/` antes de hacer públicos archivos que puedan contener datos personales.
- Utiliza datos de prueba o anonimizados para demostraciones académicas.
- Documenta las limitaciones de los datos y no generalices conclusiones fuera de la población analizada.
- No utilices la clasificación experimental como único criterio para seleccionar o descartar contratistas.

## 10. Estado y trabajo futuro

Para fortalecer el proyecto se recomienda:

1. Verificar las instrucciones de instalación con un entorno limpio y documentar las versiones reales de las dependencias.
2. Añadir pruebas de funcionamiento para los flujos principales de cliente, contratista y trabajador.
3. Incorporar capturas de pantalla propias del prototipo y de las etapas realizadas en MinedApp.
4. Evaluar una fuente de datos más cercana a proyectos de construcción, ejecución de obras y contratación de trabajadores.
5. Definir con el equipo una variable objetivo que responda a una necesidad real de ObraTech antes de considerar una predicción para producción.

## 11. Referencias

- Repositorio del proyecto ObraTech: https://github.com/juancitomiranda6-2005/Obratech
- Datos Abiertos de Colombia, conjunto CCE SECOP II: https://www.datos.gov.co/Gastos-Gubernamentales/CCE-secop-ii/tjbh-5nnb
- Guía práctica para completar los entregables del Proyecto de Aula, asignatura Minería de Datos I.

---

**Proyecto de Aula · ObraTech · Minería de Datos I**
# Entregable-1
