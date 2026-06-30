# Renewable Energy Operations Intelligence

## Andes Solar I

Solución integral de Business Intelligence para el monitoreo operativo de una planta solar fotovoltaica simulada.

El proyecto integra datos meteorológicos reales, automatización de procesos, almacenamiento estructurado, modelado relacional, medidas DAX y visualización en Power BI.

> **End-to-end Business Intelligence solution for a simulated solar power plant, integrating weather APIs, n8n automation, Google Sheets, Power Query, data modeling, DAX and Power BI dashboards.**

---

## Descripción del proyecto

**Renewable Energy Operations Intelligence** fue desarrollado como un proyecto integrador orientado a demostrar la construcción de una solución tecnológica de medición y análisis de datos de punta a punta.

El caso representa una planta solar fotovoltaica ficticia denominada **Andes Solar I**, ubicada en la provincia de Córdoba, Argentina.

La solución permite analizar:

* generación energética real y esperada;
* eficiencia operacional;
* disponibilidad de equipos;
* eventos de downtime;
* alertas operativas;
* actividades de mantenimiento;
* variables meteorológicas;
* relación entre clima y rendimiento energético.

El proyecto abarca todo el ciclo de desarrollo, desde la definición del problema y la estructuración de los datos hasta la automatización, el modelado, la validación y el diseño del producto final para el usuario.

---

## Objetivo

Diseñar una solución de Business Intelligence que centralice datos climáticos y operativos para facilitar el monitoreo y análisis del desempeño de una planta solar fotovoltaica.

Los principales objetivos fueron:

* integrar información proveniente de diferentes fuentes;
* automatizar la incorporación de datos meteorológicos;
* construir un modelo de datos relacional;
* desarrollar indicadores de rendimiento;
* analizar desvíos entre generación real y esperada;
* monitorear fallas, alertas y mantenimiento;
* diseñar tableros diferenciados según el tipo de usuario;
* construir una experiencia de navegación clara y consistente.

---

## Arquitectura de la solución

```text
Open-Meteo API
       ↓
      n8n
       ↓
 Google Sheets
       ↓
 Publicación Web
       ↓
 Power Query
       ↓
 Modelo de datos
       ↓
 Medidas DAX
       ↓
 Power BI
       ↓
 Tableros de gestión
```

### Capas del proyecto

1. **Fuente meteorológica**
   Datos climáticos históricos obtenidos mediante Open-Meteo.

2. **Automatización**
   Flujo desarrollado en n8n para consultar la API, transformar los datos, verificar fechas existentes y agregar nuevos registros.

3. **Almacenamiento**
   Google Sheets utilizado como repositorio estructurado de las tablas del proyecto.

4. **Integración**
   Cada tabla fue publicada individualmente y conectada con Power BI mediante el conector Web.

5. **Transformación**
   Limpieza y tipado de datos mediante Power Query.

6. **Modelado**
   Construcción de un modelo relacional con tablas de dimensiones y tablas de hechos.

7. **Cálculo**
   Desarrollo de medidas DAX para producción, eficiencia, clima, alertas, mantenimiento y downtime.

8. **Visualización**
   Diseño de tres tableros orientados a diferentes niveles de análisis.

---

## Tableros desarrollados

### 1. Resumen Ejecutivo

Presenta una visión consolidada del desempeño general de la planta.

Incluye indicadores de:

* energía generada;
* energía esperada;
* eficiencia;
* disponibilidad operacional;
* alertas activas;
* evolución mensual;
* desvíos de producción.

![Dashboard Ejecutivo](images/dashboard-ejecutivo.png)

---

### 2. Resumen Operativo y de Mantenimiento

Permite analizar el comportamiento de los equipos, los eventos operativos y las tareas de mantenimiento.

Incluye:

* desempeño por equipo;
* horas de downtime;
* causas de inactividad;
* alertas por prioridad;
* mantenimiento preventivo y correctivo;
* costos y duración de mantenimiento.

![Dashboard Operativo](images/dashboard-operativo.png)

---

### 3. Clima y Rendimiento

Analiza la relación entre las condiciones meteorológicas y la producción de energía.

Incluye:

* irradiancia solar;
* temperatura;
* nubosidad;
* velocidad del viento;
* generación energética;
* eficiencia;
* comportamiento mensual.

![Dashboard de Clima y Rendimiento](images/dashboard-clima-rendimiento.png)

---

## Workflow de automatización

El flujo de n8n fue diseñado para:

1. iniciar el proceso de actualización;
2. consultar la API de Open-Meteo;
3. transformar la respuesta en registros tabulares;
4. consultar las fechas existentes en Google Sheets;
5. identificar registros nuevos;
6. incorporar únicamente fechas no almacenadas previamente.

![Workflow n8n](images/n8n-workflow.png)

---

## Modelo de datos

El modelo fue diseñado con una estructura dimensional orientada a esquema estrella.

### Tablas de dimensiones

* `Dim_Date`
* `Dim_Location`
* `Dim_Equipment`
* `Dim_Alerts`
* `Dim_Priority`
* `Dim_Maintenance`

### Tablas de hechos

* `Fact_EnergyProduction`
* `Fact_Weather_API`
* `Fact_Downtime`
* `Fact_Alerts`
* `Fact_Maintenance`

### Tablas auxiliares

* `_Medidas`
* `Control_Actualizacion`

Las relaciones son activas, con cardinalidad uno a muchos y dirección de filtro simple desde las dimensiones hacia las tablas de hechos.

![Modelo de datos Power BI](images/power-bi-data-model.png)

---

## Tecnologías utilizadas

* Power BI
* Power Query
* DAX
* n8n
* Google Sheets
* Open-Meteo API
* Modelado dimensional
* Automatización de procesos
* Inteligencia artificial generativa como herramienta de apoyo

---

## Datos reales y datos simulados

El proyecto combina datos meteorológicos reales con datos operativos sintéticos.

### Datos reales

* temperatura;
* irradiancia solar;
* nubosidad;
* velocidad del viento;
* período meteorológico;
* ubicación geográfica.

### Datos simulados

* generación esperada;
* generación real;
* eficiencia operacional;
* downtime;
* alertas;
* mantenimiento;
* costos;
* prioridades;
* estados operativos.

Los datos simulados fueron generados mediante reglas de negocio diseñadas para mantener coherencia entre las condiciones climáticas y el comportamiento operativo de la planta.

---

## Metodología de simulación

Ante la ausencia de datos industriales reales, se desarrolló un entorno sintético basado en:

* capacidad instalada;
* características de los equipos;
* variables meteorológicas;
* disponibilidad operacional;
* fallas;
* mantenimiento;
* pérdidas técnicas;
* eventos anómalos.

La lógica conceptual utilizada fue:

```text
Generación real =
Capacidad instalada
× Recurso solar
× Eficiencia técnica
× Disponibilidad
× Ajuste climático
− Pérdidas operativas
```

La inteligencia artificial generativa fue utilizada como herramienta de apoyo para:

* estructurar reglas de negocio;
* desarrollar scripts;
* proponer escenarios operativos;
* revisar coherencia lógica;
* documentar el proceso.

Los supuestos, ajustes y decisiones finales fueron revisados e integrados por la autora.

---

## Transformaciones realizadas

Las principales transformaciones en Power Query fueron:

* conexión mediante fuente Web;
* promoción de encabezados;
* asignación de tipos de datos;
* uso de configuración regional para números decimales;
* eliminación de filas en blanco;
* eliminación de duplicados;
* control de valores nulos;
* estandarización de campos;
* validación de claves y fechas.

También se crearon columnas adicionales dentro de Power BI para:

* traducción de categorías;
* ordenamiento de prioridades;
* abreviaturas de meses;
* clasificación de equipos;
* clasificación de mantenimiento;
* presentación de alertas en español.

---

## Navegación y experiencia de usuario

La solución está compuesta por tres páginas principales conectadas mediante botones de navegación.

Cada página dispone de filtros independientes de:

* año;
* mes;
* tipo de equipo, cuando corresponde.

Los principales indicadores responden dinámicamente a las selecciones realizadas.

También se incorporaron:

* tooltips estándar enriquecidos;
* selección múltiple;
* control de interacciones entre visuales;
* fecha y hora de actualización;
* visualización del período analizado;
* jerarquía visual consistente;
* navegación orientada al tipo de usuario.

---

## Principales desafíos técnicos

Durante el desarrollo se abordaron los siguientes desafíos:

* definir una arquitectura completa de datos;
* integrar información climática real con datos operativos simulados;
* automatizar la incorporación de nuevos registros;
* migrar y conectar tablas publicadas desde Google Sheets;
* definir correctamente tipos y formatos de datos;
* construir un modelo relacional consistente;
* crear tablas de dimensiones a partir de tablas de hechos;
* mantener categorías visibles en los gráficos;
* desarrollar medidas DAX;
* resolver formatos y unidades de medida;
* diseñar indicadores de producción, eficiencia y disponibilidad;
* construir navegación y controles;
* diseñar una experiencia de usuario diferenciada;
* validar coherencia entre clima, producción, eficiencia y downtime.

---

## Validación y control de calidad

Los controles realizados incluyeron:

* eliminación de registros duplicados;
* eliminación de filas en blanco;
* revisión de tipos de datos;
* control de valores nulos;
* validación de claves y relaciones;
* revisión del modelo dimensional;
* prueba de navegación;
* validación de filtros de año y mes;
* prueba de selección múltiple;
* control de actualización;
* revisión visual de la relación entre clima, generación y eficiencia.

No se realizó una conciliación formal automatizada de totales entre tablas y visualizaciones, lo que se identifica como una posible mejora futura.

---

## Alcance y limitaciones

Este proyecto representa una prueba de concepto analítica y no una implementación industrial real.

Actualmente no incluye:

* integración con SCADA;
* sensores físicos;
* infraestructura IoT;
* telemetría industrial;
* streaming de datos;
* actualización en tiempo real;
* modelos predictivos;
* machine learning;
* conexión directa con una base de datos industrial;
* calibración contra una planta real.

La solución se concentra en la **capa de integración, modelado, medición y visualización de datos**.

Los resultados no deben interpretarse como estimaciones de ingeniería, pronósticos energéticos ni evaluaciones económicas de una planta real.

---

## Mejoras futuras

El proyecto puede evolucionar mediante:

* incorporación de un caso real;
* integración con SCADA e IoT;
* conexión con sensores;
* actualización programada o en tiempo real;
* migración desde Google Sheets hacia una base de datos;
* integración con Power BI Service;
* automatización de alertas;
* incorporación de granularidad horaria;
* desarrollo de drillthrough;
* tooltips personalizados;
* indicadores económicos;
* cálculo de emisiones evitadas;
* modelos predictivos;
* análisis de fallas;
* mejora del resaltado visual de anomalías.

---

## Competencias demostradas

El proyecto evidencia capacidad para:

* estructurar problemas de negocio;
* diseñar soluciones digitales de medición;
* construir procesos ETL;
* integrar APIs;
* automatizar flujos;
* modelar datos;
* desarrollar medidas DAX;
* diseñar KPIs;
* validar información;
* desarrollar productos en Power BI;
* diseñar experiencias de usuario;
* documentar soluciones técnicas y ejecutivas;
* utilizar inteligencia artificial de forma crítica;
* gestionar un proyecto tecnológico de punta a punta.

---

## Documentación

La documentación completa se encuentra disponible en la carpeta `docs`.

* [Documento Ejecutivo](docs/documento-ejecutivo.pdf)
* [Documento Técnico](docs/documento-tecnico.pdf)

El documento ejecutivo presenta el proyecto desde una perspectiva de negocio.

El documento técnico describe la arquitectura, las fuentes, las transformaciones, el modelo de datos, las medidas, la simulación y las validaciones realizadas.

---

## Estructura del repositorio

```text
renewable-energy-operations-intelligence/
│
├── README.md
│
├── docs/
│   ├── documento-ejecutivo.pdf
│   └── documento-tecnico.pdf
│
└── images/
    ├── dashboard-ejecutivo.png
    ├── dashboard-operativo.png
    ├── dashboard-clima-rendimiento.png
    ├── n8n-workflow.png
    ├── power-bi-data-model.png
    └── fact-weather-api.png
```

---

## Autora

**Laura Agostina Spena**

Proyecto integrador de análisis de datos, automatización, Business Intelligence y visualización aplicada al sector de energías renovables.

---

## Nota

Este repositorio tiene fines académicos y de portafolio profesional.

La planta, los equipos y los datos operativos son ficticios. Los datos meteorológicos utilizados provienen de fuentes abiertas y fueron integrados con fines analíticos.
