# Manual de Usuario - Modelo Analítico de Seguimiento MEGAS

**Proyecto:** Modelo de Gestión Gestión transformación tecnológica y de Procesos  
**Cliente:** Grupo MEGAS   
**Preparado por:** Equipo Analítica y Tecnología QCS  
**Actualización:** Septiembre 2026 

---

## Contexto

Como parte de la Fase 2 del proyecto, se diseñó e implementó un *tablero de control en Power BI* para el monitoreo de los procesos core del Grupo MEGAS. Esta solución consolida indicadores clave de negocio (KPI) y métricas de desempeño mediante visualizaciones desarrolladas a partir del *mockup* aprobado por la gerencia de MEGAS durante la fase 2 del proyecto.

## Arquitectura y Proceso ETL

Para garantizar la integridad y trazabilidad del flujo de datos, el modelo se rige bajo los siguientes principios:

* **Extracción:** La captación de datos se ejecuta mediante scripts de Python a partir de dos orígenes principales: los archivos manuales alojados en el sitio de SharePoint definido para el proyecto y las fuentes de información con conexión vía API disponible. 

* **Transformación:** El procesamiento, limpieza y estandarización de los datos se realiza en Python aplicando la arquitectura Medallion (capas Bronce, Plata y Oro). Por su parte, el cálculo de las métricas de negocio se gestiona directamente en Power BI mediante lenguaje DAX. 

* **Carga:** El modelo de datos procesado se integra desde Power Query hacia la capa de visualización en Power BI. 

> **Nota de Despliegue:** La solución incluye un componente gráfico desarrollado en **Power BI Desktop** en *formato local* (offline). La instalación, configuración y publicación en entornos corporativos (como Power BI Service) es responsabilidad del usuario final.

---

## Alcance 

El Modelo Analítico de Seguimiento contempla los siguientes componentes para su correcta operación:

* **Sitio en SharePoint** : Directorio destinado al almacenamiento de las fuentes de información manuales. Mantiene la misma estructura de la solución desplegada en el servidor físico. Tras la ejecución del pipeline (orquestador principal), este espacio almacena una copia de los datos procesados correspondientes a las capas Bronce, Plata y Oro, junto con sus respectivos logs de ejecución. 

* **Códigos en Python** : Conjunto de rutinas encargadas de la extracción, transformación y carga de los datos (procesos ETL). La instalación y despliegue de la herramienta se centra en la configuración de estos scripts. Es importante destacar que el modelo analítico no genera nueva información transaccional; su alcance se limita estrictamente a transformar, estructurar y consolidar los datos ya existentes.

* **Archivo `.pbix`**: Contiene la capa de visualización y el modelo de datos históricos procesados mediante el flujo ETL, abarcando un periodo de los últimos 24 meses.

* **Documentación Técnica**: Este portal interactivo que proporciona una explicación detallada sobre la arquitectura, configuración y funcionamiento de cada uno de los componentes de la solución.

---

## Calidad de la Información Histórica

Para la construcción del tablero, se ejecutó un proceso de evaluación sobre los datos históricos correspondientes al periodo comprendido entre **enero de 2025 y julio de 2026**, los cuales fueron validados en conjunto con los equipos funcionales de MEGAS.

Es importante señalar que, debido al alto componente operativo manual en la captura original de la información, las cifras presentadas podrían mostrar variaciones frente a otros reportes preexistentes de la compañía. Por lo tanto, es responsabilidad exclusiva de MEGAS liderar la conciliación, estabilización y depuración tanto de los datos fuente como de sus procesos de origen, garantizando así que el tablero consuma información con el más alto estándar de calidad posible.


