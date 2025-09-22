# Plan de Calidad – Proyecto *Neural Quorum Governance* (stellar-community-fund-contracts)

**Proyecto:** Neural Quorum Governance (parte de Stellar Community Fund)
**Repositorio:** *stellar/stellar-community-fund-contracts* ([GitHub][1])
**Versión del Plan de Calidad:** 1.0
**Fecha de Inicio:** \[poner fecha de comienzo real]
**Responsables principales:**

* Gerente de Calidad: \ Ariadna Lopez
* Líder Técnico Rust / Soroban: \Evelyn Santiago
* Responsable Off-chain / Infraestructura: \Uriel Arcadio
* QA / Tester: \Kevin Osorio

---

## 1. Objetivos de Calidad específicos

1. Garantizar que los contratos inteligentes y módulos off-chain sean seguros, especialmente para votaciones y cálculo de poderes: evitar vulnerabilidades conocidas de Rust / Soroban.
2. Cumplir con los requisitos funcionales del repositorio (votación on-chain, cálculo de “neurona”, ayuda off-chain) correctamente, sin inconsistencias entre lo que la documentación dice y lo que el código hace.
3. Alta calidad en la documentación: README completo, CONTRIBUTING claro, documentación específica de los contratos (interfaces, eventos, errores, tests).
4. Mantener alta cobertura de pruebas unitarias + de integración, tanto para los contratos como para los módulos off-chain.
5. Procesos reproducibles de compilación, pruebas y despliegue en ambientes de test / staging / producción en Soroban / Stellar.
6. Rendimiento aceptable (por ejemplo, latencia, uso de gas / recursos, costos de transacción), si aplica.

---

## 2. Estándares y Referencias

* Estilo de Rust recomendado por la comunidad / Soroban best practices.
* Guías de seguridad en Soroban / contratos inteligentes (por ejemplo OWASP Top 10 smart contract vulnerabilities).
* Uso de linters / formateadores de Rust (rustfmt, clippy).
* Versionado semántico para los contratos / cambios mayores de interfaz.
* Especificaciones de documentación: por contrato, eventos, errores, funciones públicas, etc.

---

## 3. Roles y Responsabilidades adaptados

| Rol                            | Persona / Equipo | Tareas específicas                                                                                                                                                      |
| ------------------------------ | ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Gerente de Calidad             |Ariadna                | Asegurar que todo el plan se cumpla; aprobar versiones importantes; coordinación con seguridad auditoría.                                                               |
| Líder Técnico (Rust / Soroban) | Evelyn              | Supervisar desarrollo de contratos; definir interfaces y APIs; revisión de código; optimización de gas y rendimiento.                                                   |
| Responsable Off-chain          | Uriel               | Garantizar que los módulos off-chain (por ejemplo utilitarios, scripts) cumplan estándares de seguridad, pruebas e integración.                                         |
| QA / Tester                    | Kevin               | Escribir y ejecutar pruebas unitarias, de integración; tests de seguridad; pruebas de contrato en ambientes de prueba de Soroban; detectar regresiones.                 |
| DevOps / Infraestructura       | Ariadna               | Configurar CI/CD para contratos y módulos off-chain; desplegar en testnet / staging; monitoreo; rollback; control de versiones.                                         |
| Documentación / Comunidad      |Evelyn| Mantener README, CONTRIBUTING, guía de contratos; asegurar que los desarrolladores externos puedan entender cómo contribuir; actualizar documentación con cada release. |

---

## 4. Procesos y Actividades de Calidad adaptados

| Fase                  | Actividades concretas                                                                                                                                                                                                                     |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Planeación            | Revisar los requerimientos actuales del repo: qué hacen los contratos, off-chain, qué módulos faltan, qué tests existentes. Establecer criterios de aceptación para cada contrato. Planificar cobertura de pruebas mínima.                |
| Diseño / Arquitectura | Crear diagramas de arquitectura del sistema (on-chain/off-chain). Documentar decisiones de diseño (por ejemplo, por qué se eligió cierto mecanismo de votación, estructuras de datos).                                                    |
| Desarrollo            | Usar `rustfmt` y `clippy` para mantener estilo. Revisiones de Pull Request obligatorias por al menos un desarrollador experto en Soroban/Rust. Escribir tests de unidad y de integración. Verificar cómo los contratos consumen recursos. |
| Integración / Pruebas | Probar contratos en testnet de Stellar / Soroban; pruebas que simulen votaciones reales; integración del módulo off-chain con los contratos; pruebas de seguridad automatizadas.                                                          |
| Documentación         | Documentar cada contrato: interfaz pública, errores posibles, eventos emitidos. Mantener guides: cómo desplegar, cómo correr tests, cómo contribuir, cómo auditar cambios.                                                                |
| Deploy / Producción   | Pipeline CI/CD para compilar los contratos, desplegarlos en entornos seguros; monitoreo del contrato desplegado (gas usado, fallos). Plan de rollback si hay bug crítico.                                                                 |
| Mejora Continua       | Post-mortems al detectar bugs; registrar métricas (número de bugs, tiempo de corrección, cobertura, latencia); ajustar procesos de desarrollo basados en feedback.                                                                        |

---

## 5. Métricas de Calidad adaptadas

| Métrica                                             | Meta específica                                                                          |
| --------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Cobertura de tests (contratos + off-chain)          | ≥ 85 %                                                                                   |
| Linter / formato / warnings de compilación          | 0 advertencias en `clippy` / compilación limpia                                          |
| Número de vulnerabilidades críticas                 | 0 en producción; tolerancia 0 para errores críticos que comprometan fondos o votaciones. |
| Tiempo de revisión de PR                            | < 48 horas para revisores asignados                                                      |
| Tiempo de despliegue testnet → producción           | Automatizado; idealmente < 1 día si todo está verificado                                 |
| Documentación de contratos                          | Cada contrato con su interfaz, errores y ejemplos de uso documentados                    |
| Latencia o costo estimado de operación del contrato | Dependiente del uso; presupuesto de gas / recurso estimado documentado                   |

---

## 6. Gestión de Riesgos adaptados

| Riesgo                                                                                                           | Probabilidad | Impacto    | Mitigación                                                                                                                                             |
| ---------------------------------------------------------------------------------------------------------------- | ------------ | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Bug que permita manipular votaciones / poderes de neuronas                                                       | Medio-alto   | Muy alto   | Auditorías internas & externas; pruebas exhaustivas; revisión de seguridad; pruebas de fuzz si aplicable.                                              |
| Incompatibilidades entre off-chain y on-chain (por versión del contrato, tipo de dato, errores de serialización) | Medio        | Alto       | Versiones de contrato bien definidas; integración continua; pruebas de integración real; usar especificaciones claras.                                 |
| Cambios en la infraestructura de Stellar / Soroban que rompan compatibilidad                                     | Medio        | Medio-alto | Mantener seguimiento de versiones de Soroban; pruebas con actualizaciones; definir versiones de contrato con compatibilidad hacia atrás si es posible. |
| Documentación desactualizada                                                                                     | Alta         | Medio      | Revisión de documentación como parte de PR; plantilla que obliga actualizar docs si cambio de API; responsabilidad clara.                              |
| Alto consumo de gas / recursos                                                                                   | Medio        | Medio      | Perfilado de contrato; optimización de código; benchmarks; límites de gas documentados.                                                                |

---

## 7. Herramientas y entorno adaptados

* **Repositorio GitHub** del proyecto: *stellar/stellar-community-fund-contracts* ([GitHub][1])
* CI/CD: usar GitHub Actions (o similar) para compilar contratos, ejecutar tests unitarios, pruebas de integración, verificación de linters, ejecución de pruebas de seguridad.
* Herramientas de Rust: `rustc`, `cargo test`, `cargo fmt`, `clippy`.
* Herramientas de seguridad: escaneo de dependencias (por ejemplo Dependabot), análisis estático, quizás uso de fuzz testing si aplicable.
* Entornos de despliegue: testnet Soroban; staging si hay versión off-chain que interactúa; producción.
* Documentación: README.md, CONTRIBUTING.md ya existen, pero añadir documentación específica de contratos (interfaces, ejemplos), CHANGELOG.md; guías de despliegue.

---

## 8. Estructura de Documentación adaptada

Estructura sugerida en el repositorio:

```
/README.md
/CONTRIBUTING.md
/CHANGELOG.md
/docs/
    arquitectura.md
    contratos/
        governance_contract.md
        scf_token_contract.md
        governor_contract.md
    offchain.md
    deploy.md
/tests/
    unit/
    integration/
/src/contracts/
/src/neurons/
/src/offchain/
/scripts/
/ci/   (o workflows en .github/workflows/)
```

* Cada contrato documentado en su fichero dentro de `/docs/contratos/`.
* Guía de despliegue (`deploy.md`) que indique cómo compilar, desplegar en testnet, migraciones, etc.
* Ejemplos de uso: scripts / ejemplos off-chain que muestren cómo interactuar con los contratos.

---

## 9. Criterios de Aceptación / Salida

Antes de hacer un release oficial (por ejemplo versión v1.0):

* Todos los tests unitarios y de integración pasan.
* Cobertura de pruebas ≥ 85 %.
* No hay warnings críticos de compilación (`clippy`) / errores de lint.
* Documentación actualizada para todos los cambios en interfaces de contratos / eventos.
* Revisión de seguridad completada si hay cambios significativos de contrato.
* Pruebas desplegadas en testnet sin errores críticos.
* Pull requests revisados por al menos 1 persona con experiencia en Soroban/Rust.

---

## 10. Cronograma Adaptado

| Hito                                  | Tiempo estimado\*   | Actividades                                                                                                              |
| ------------------------------------- | ------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Inicio - evaluación del estado actual | Día 0-7             | Auditoría ligera del repositorio; identificar gaps de pruebas, documentación, estilo.                                    |
| Sprint 1                              | Semanas 1-2         | Mejorar pruebas unitarias; aplicar `rustfmt` y `clippy`; documentar contratos principales; establecer pipelines básicos. |
| Sprint 2                              | Semanas 3-4         | Integración off-chain/on-chain; pruebas de integración; ejemplos de uso; revisión de seguridad básica.                   |
| Revisión intermedia                   | Semana 5            | Validación con stakeholders; revisión de métricas de calidad; ajustes.                                                   |
| Beta Test / Deploy en testnet         | Semana 6            | Despliegue en testnet; pruebas de uso real; validación de performance / gas; detectar problemas en entorno real.         |
| Release v1.0                          | Semana 8            | Lanzamiento oficial del contrato / código; documentación completa; monitoreo en producción.                              |
| Retrospectiva / Mejora Continua       | Después del release | Analizar lo que funcionó / lo que no; capturar lecciones aprendidas; planear mejoras para versiones futuras.             |

