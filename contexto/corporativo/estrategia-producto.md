---
title: Estrategia de Producto — Coverwise
author: Claude (Cowork)
created: 2026-05-06
last_modified: 2026-05-06
last_modified_by: Claude (Cowork)
version: 1.0
modification_count: 1
status: active
---

# Estrategia de Producto — Coverwise

> Describe la dirección estratégica del producto: visión, objetivos, OKRs y contexto de mercado.
> Leer al inicio de cualquier tarea de specs, discovery o planificación estratégica.

---

## Visión del producto

**Visión:** Que cualquier asegurado NexHealth sepa al instante si su prestación está cubierta — sin llamar, sin esperar, sin formularios.

---

## Objetivos estratégicos

| # | Objetivo | Indicador de éxito | Horizonte |
|---|----------|-------------------|-----------|
| O1 | Reducir la carga del call center en consultas de cobertura | Llamadas por cobertura -30% | Q3 2026 |
| O2 | Mejorar la experiencia del asegurado en momentos críticos de salud | NPS del asegurado +10 puntos | Q4 2026 |
| O3 | Aumentar la retención en el segmento joven (25-40 años) | Churn rate segmento digital -15% | Q4 2026 |

---

## OKRs activos

### Objective: Hacer que el asegurado resuelva sus dudas de cobertura sin intervención humana

| Key Result | Baseline | Target | Fecha | Status |
|-----------|----------|--------|-------|--------|
| KR1: % de consultas de cobertura resueltas en autoservicio digital | 12% | 45% | Sep 2026 | `on_track` |
| KR2: Reducción de llamadas por cobertura al call center | 8.200/mes | 5.700/mes | Sep 2026 | `on_track` |
| KR3: NPS post-consulta de cobertura | 28 | 42 | Dic 2026 | `at_risk` |

---

## Contexto de mercado y usuarios

**Segmento de usuarios:** Asegurado joven NexHealth (25-40 años), plan digital, mobile-first. Acostumbrado a resolver todo desde el teléfono. Baja tolerancia a la fricción: si no obtiene respuesta en segundos, llama o simplemente no se atiende.

**Problema que resolvemos:** El asegurado no sabe si su prestación está cubierta en el momento en que la necesita — justo antes de ir al médico, a la clínica o a urgencias. La respuesta estándar hoy es llamar al call center (tiempo de espera promedio: 7 minutos) o navegar una app con un chatbot que solo entiende palabras clave y responde con formularios PDF.

**Contexto competitivo:** Las aseguradoras tradicionales no tienen solución de lenguaje natural — sus bots son árboles de decisión disfrazados. Las insurtechs más avanzadas (Bupa Digital, Vida Cámara) tienen apps modernas pero siguen requiriendo búsqueda manual por código de prestación. Coverwise apunta a ser el primero en responder "¿me cubre esto?" en lenguaje natural, sin código, sin manual.

---

## Restricciones estratégicas

| Restricción | Detalle |
|-------------|---------|
| Sistema core legacy | Los datos de cobertura viven en un sistema de pólizas con 15 años de antigüedad. Las APIs disponibles son REST pero con latencia alta (~2s) y esquema de datos complejo. Coverwise debe abstraer esta complejidad. |
| Regulación sanitaria | En Chile y Colombia, las respuestas sobre cobertura tienen implicancias legales. Coverwise debe ser claro en que la respuesta es orientativa y no reemplaza la resolución formal de la aseguradora. |
| Privacidad de datos | Los datos de póliza son sensibles. Coverwise no puede almacenar el historial de consultas de forma identificada sin consentimiento explícito del asegurado. |
| Tiempo al mercado | El equipo tiene presupuesto para 3 meses de engagement con TW. La solución debe ser deployable antes del término del contrato. |

---

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | 2026-05-06 | Claude (Cowork) | Población inicial con contexto del caso ficticio NexHealth/Coverwise |
