# Plan de Calidad de Software

**Código de Versión:** V1.0
**Fecha:** 24 de septiembre de 2025
**Autor(es):** Equipo de Desarrollo Neural Quorum Governance - Stellar Community Fund

---

## 1. Introducción y Alcance

El presente documento define el **Plan de Calidad de Software** para el proyecto **Neural Quorum Governance**, un sistema de gobernanza descentralizada para la administración de fondos comunitarios sobre la plataforma Stellar.

El objetivo es asegurar que el producto final cumpla con los requisitos funcionales y no funcionales, así como con los más altos estándares de calidad, seguridad, transparencia y confiabilidad, siguiendo las buenas prácticas de desarrollo y el modelo **MoProSoft**.

Este plan se aplicará a todas las fases del ciclo de vida del desarrollo de **Neural Quorum Governance**, desde la planificación hasta la implementación, auditoría de contratos inteligentes y mantenimiento.

---

## 2. Referencias Normativas - Modelo MoProSoft

Este plan se basa en el modelo **MoProSoft (Modelo de Procesos para la Industria del Software)**, orientado a la mejora continua y evaluación de procesos de desarrollo y mantenimiento de software.

Las directrices clave del modelo que se aplicarán son:

* **Gestión de Proyectos (GPR):** Planificación, seguimiento y control de las actividades del desarrollo de contratos inteligentes y front-end de gobernanza.
* **Gestión de Recursos (GRC):** Asignación de personal especializado en blockchain, desarrollo de smart contracts y pruebas de seguridad.
* **Operación (OPE):** Desarrollo y despliegue de contratos inteligentes y la interfaz de gobernanza de usuarios.
* **Gestión de la Calidad (GCA):** Aseguramiento y control de calidad en cada etapa, con especial énfasis en seguridad y cumplimiento de reglas de quorum.

---

## 3. Gestión de la Calidad

### 3.1. Procedimientos y Actividades

* **Revisiones de Requisitos:** Validación con stakeholders de los mecanismos de gobernanza, votación y distribución de fondos.
* **Revisiones de Diseño:** Inspección de la arquitectura de contratos inteligentes, flujos de votación y seguridad criptográfica.
* **Inspecciones de Código (Peer Review):** Revisión cruzada del código de contratos inteligentes en Rust y del front-end en Vue.js.
* **Pruebas de Software:**

  * *Pruebas Unitarias:* Validación de funciones de smart contracts, votaciones, cálculos de quorum y pagos.
  * *Pruebas de Integración:* Verificación de interacción entre contratos, blockchain Stellar y la interfaz web.
  * *Pruebas de Sistema:* Validación del sistema completo contra los requisitos de gobernanza.
  * *Pruebas de Seguridad:* Auditoría de vulnerabilidades en smart contracts, simulación de ataques y validación de firmas digitales.
  * *Pruebas de Usabilidad:* Evaluación de la interfaz de votación y panel de control de la comunidad.
* **Control de Cambios:** Toda modificación en requisitos, diseño o código seguirá un proceso formal de solicitud, evaluación, aprobación y verificación.

### 3.2. Defectos y Errores de Software

Clasificación de defectos para priorizar su resolución:

* **Crítico (P1):** Riesgo de pérdida de fondos o fallo en la gobernanza (ej. contratos no ejecutan pagos correctamente). Corrección inmediata.
* **Mayor (P2):** Afecta funcionalidades importantes de votación o quorum sin comprometer fondos (ej. conteo de votos incorrecto).
* **Menor (P3):** Errores en visualización de interfaz, íconos o reportes no críticos.
* **Sugerencia (P4):** Mejoras en la experiencia de usuario o propuestas de optimización de código.

### 3.3. Métricas de Calidad

Se medirán y analizarán las siguientes métricas:

* **Defectos por Línea de Código (Defect Density):** Defectos/KLOC en smart contracts y front-end.
* **Tasa de Aprobación de Pruebas (Test Pass Rate):** (Pruebas Aprobadas / Totales) x 100.
* **MTTR (Mean Time to Repair):** Tiempo promedio de corrección de defectos críticos.
* **Cobertura de Código (Code Coverage):** Porcentaje de código de smart contracts cubierto por pruebas unitarias.
* **Defectos por Módulo:** Identifica los contratos o componentes de interfaz más propensos a fallos.

---

## 4. Roles y Responsabilidades

* **Gerente de Proyecto:** Supervisión general del plan de calidad y coordinación de auditorías.
* **Ingeniero de Calidad:** Diseña y supervisa ejecución de pruebas y procedimientos de QA en blockchain y front-end.
* **Analista de Requisitos:** Garantiza claridad y consistencia en los requerimientos de gobernanza y reglas de quorum.
* **Equipo de Desarrollo:** Implementa contratos inteligentes en Rust y la interfaz web en Vue.js; realiza pruebas unitarias.
* **Equipo de Pruebas (QA):** Ejecuta pruebas de integración, sistema y seguridad; reporta defectos y vulnerabilidades.

---

## 5. Herramientas

* **Gestión de Proyectos:** Jira, Trello.
* **Control de Versiones:** Git y GitHub.
* **Reporte de Defectos:** Jira.
* **Automatización de Pruebas:** Jest para front-end, Soroban CLI y herramientas de testing de smart contracts para Stellar.

### 5.1. Procedimiento de Gestión de Defectos

1. **Identificación:** El equipo de QA documenta el defecto en Jira (pasos, resultado esperado y obtenido).
2. **Clasificación:** El gerente o líder técnico clasifica el defecto según severidad (P1–P4).
3. **Asignación:** Se asigna a un desarrollador del módulo afectado.
4. **Corrección:** El desarrollador corrige el defecto.
5. **Verificación:** QA realiza pruebas unitarias y de integración sobre la corrección.
6. **Cierre:** QA valida la corrección y cierra la incidencia.

### 5.2. Glosario de Términos

* **Bug:** Error o falla en el software.
* **Defecto:** Error detectado durante desarrollo o pruebas.
* **Métrica:** Indicador cuantitativo para medir calidad.
* **MoProSoft:** Modelo de Procesos para la Industria del Software.
* **Quorum:** Porcentaje mínimo de votos necesarios para validar decisiones.
* **Soroban:** Entorno de desarrollo para contratos inteligentes en Stellar.

---

## 6. Conclusión

El plan de calidad de **Neural Quorum Governance** asegura que el proyecto cumpla con los estándares de seguridad, transparencia y confiabilidad propios de sistemas de gobernanza descentralizada en Stellar.

Se centra en establecer procesos claros de desarrollo, pruebas y auditoría de contratos inteligentes, garantizando un sistema robusto, escalable y seguro.

Al aplicar métricas de desempeño, revisiones de código y validaciones de seguridad, se busca minimizar riesgos, proteger los fondos comunitarios y ofrecer una experiencia confiable para los miembros de la comunidad.

En conclusión, el plan de calidad no solo fortalece la confianza de los usuarios y la comunidad, sino que también contribuye al **éxito y sostenibilidad** del proyecto dentro del Stellar Community Fund.

