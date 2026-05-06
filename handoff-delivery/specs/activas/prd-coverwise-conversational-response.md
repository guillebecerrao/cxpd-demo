---
title: "PRD — Coverwise Conversational Response"
author: "Claude (Handoff facilitador)"
created: 2026-05-06
last_modified: 2026-05-06
last_modified_by: "Claude (Handoff facilitador)"
version: 0.1
modification_count: 1
status: draft
type: prd
epic: "Coverwise Conversational Response"
owner: "Ignacio Fuentes (PM)"
sprint_target: "Sprint 01–04"
ost_node: "C1.1"
---

# PRD — Coverwise Conversational Response

---

## 1. Resumen ejecutivo

Coverwise es el asistente conversacional de coberturas de NexHealth. Hoy el asistente comprende la consulta del asegurado pero responde con el texto literal de la póliza — lenguaje técnico, denso, y sin indicar si la respuesta aplica al plan específico del usuario. El resultado es que el asegurado no confía en la respuesta y llama al call center de todas formas, lo que explica por qué el NPS post-consulta (KR3) está en riesgo mientras los indicadores de adopción están en verde.

Coverwise Conversational Response reemplaza la respuesta técnica por una respuesta generada por LLM: conversacional, personalizada al plan del asegurado, con un indicador de certeza explícito y una acción sugerida como siguiente paso. El objetivo es que el asegurado pueda resolver su consulta de cobertura sin necesidad de llamar — en el canal digital, con confianza suficiente para actuar.

Este PRD cubre los PBIs 01 al 05 del ciclo. La solución se valida mediante un A/B test en producción con criterio de éxito definido.

---

## 2. Contexto y problema

### Problem Statement

El asegurado de NexHealth necesita saber si su procedimiento médico está cubierto justo antes de ir al médico, clínica o urgencias. Cuando consulta a Coverwise, recibe una respuesta que no le genera suficiente claridad ni confianza para actuar sin llamar: el lenguaje es técnico, no sabe si aplica a su plan, y no tiene claro qué hacer después.

### Background

- Coverwise fue lanzado como asistente conversacional de coberturas. La adopción creció (KR1/KR2 on_track: 8.200 → target 5.700 llamadas/mes), pero la satisfacción no acompañó (KR3 at_risk: NPS 28, target 42).
- La estrategia de producto describe el problema actual explícitamente: "el bot solo entiende keywords y responde con formularios PDF". La solución actual genera respuestas directamente del texto de la póliza, sin transformación.
- No hay entrevistas de usuario en este ciclo (bypassed para la demo). Los supuestos están documentados en `ideate-validate/solution-assumptions.md`.

### Evidencia de soporte

| Fuente | Insight |
|--------|---------|
| KR3 at_risk (NPS: 28) | El canal digital es usado pero no satisface — señal directa de problema en la respuesta, no en el acceso |
| KR1/KR2 on_track | Hay adopción — el problema no es que no lleguen a Coverwise, sino que la respuesta no es suficiente |
| Estrategia de producto | "bot responde con formularios PDF" — la causa técnica del problema está documentada |
| Restricción regulatoria | Las respuestas tienen implicaciones legales — requieren disclaimer y no pueden inducir a error |

---

## 3. Objetivos y métricas

### Outcome esperado

| Métrica | Baseline actual | Target | Plazo |
|---------|----------------|--------|-------|
| NPS post-consulta de cobertura | 28 | ≥ 38 (+10 en ciclo) | Dic 2026 (primera medición: Aug 2026) |
| % de usuarios que llaman en 24h post-consulta digital | Sin baseline (a medir con A/B) | −20% vs. control | Aug 2026 |
| Tasa de adopción del CTA "siguiente paso" | Sin baseline | ≥ 25% de sesiones con respuesta positiva | Aug 2026 |

### Non-goals

- Mejorar el reconocimiento de vocabulario coloquial (B1.1) — se aborda como trabajo técnico interno del Response Engine, no como feature visible
- Eliminar el call center — la escalación inteligente (PBI-04) complementa, no reemplaza al equipo de soporte
- Almacenar historial de consultas — fuera del alcance por restricciones de privacidad (requiere consentimiento explícito, no contemplado en este ciclo)
- Soporte multilingüe — solo español en este ciclo

---

## 4. User Stories

### Persona principal

**Martina, 31 años** — Asegurada Plan Digital Plus, usuaria mobile-first. Trabaja en horario de oficina, usa la app durante el almuerzo o en el camino. Tolerancia mínima a la fricción: si no obtiene la respuesta en 30 segundos, llama. No entiende terminología médica ni de seguros — necesita que le hablen en su idioma.

### Stories

| ID | Como... | Quiero... | Para... | Prioridad |
|----|---------|-----------|---------|-----------|
| US-01 | Asegurada con consulta de cobertura | Recibir una respuesta en lenguaje claro que entienda de inmediato | Saber si puedo ir al médico sin llamar primero | Must |
| US-02 | Asegurada | Ver que la respuesta aplica específicamente a mi plan | Confiar en que no es una respuesta genérica que no aplica a mi caso | Must |
| US-03 | Asegurada con resultado "cubierto" | Saber qué hacer inmediatamente después de recibir la respuesta | No quedar con la respuesta pero sin un camino claro de acción | Should |
| US-04 | Asegurada con resultado incierto | Tener una salida digna cuando el sistema no puede responder con certeza | No quedar frustrada y tener que llamar igual, pero sin contexto | Should |
| US-05 | Asegurada con resultado "no cubierto" | Entender qué opciones tengo aunque la prestación no esté cubierta | No quedar con un "no" sin alternativas | Could |

---

## 5. Diseño funcional

### User Flow — Consulta con respuesta conversacional

```
[Asegurada abre Coverwise]
        │
        ▼
[Formula consulta en lenguaje natural]
"¿Me cubren la resonancia de rodilla?"
        │
        ▼
[Coverwise procesa]
  ├── Capa semántica: mapea vocabulario coloquial → código de procedimiento
  ├── API legacy: consulta cobertura para el plan de la asegurada
  └── LLM: genera respuesta conversacional con datos del plan
        │
        ▼
[Respuesta con 3 elementos]
  ┌─────────────────────────────────────┐
  │ ✓ Sí, está cubierta                 │
  │                                     │
  │ Tu consulta de resonancia magnética │
  │ de rodilla está cubierta bajo tu    │
  │ Plan Digital Plus. Pagas solo el    │
  │ copago de $12.000.                  │
  │                                     │
  │ [Plan Digital Plus · Alta certeza]  │
  │                                     │
  │ ¿Quieres que te ayude a encontrar  │
  │ un prestador en tu red?  [Sí →]    │
  └─────────────────────────────────────┘
        │
   ┌────┴────┐
   ▼         ▼
[Sigue CTA] [Cierra]
```

### Flujo alternativo — Certeza baja (escalación inteligente)

```
[LLM: confidence score < umbral]
        │
        ▼
[Respuesta con advertencia]
  ┌─────────────────────────────────────┐
  │ ⚠ No estoy seguro/a para tu caso   │
  │                                     │
  │ Parece que tu procedimiento podría  │
  │ estar cubierto, pero no tengo       │
  │ suficiente certeza para tu plan.    │
  │                                     │
  │ ¿Quieres que un asesor lo confirme? │
  │ Ya tiene el contexto de tu consulta.│
  │                          [Conectar] │
  └─────────────────────────────────────┘
        │
        ▼
[Handoff a asesor con payload: consulta, plan, respuesta tentativa]
```

### Edge Cases

| Escenario | Comportamiento esperado |
|-----------|------------------------|
| API legacy sin respuesta (timeout) | Mostrar mensaje de error amigable + ofrecer escalación inmediata. No mostrar respuesta incompleta. |
| LLM devuelve respuesta con confidence < umbral | Activar flujo de escalación inteligente (PBI-04) |
| Procedimiento no existe en el catálogo de coberturas | "No encontré ese procedimiento. ¿Puedes describírmelo de otra manera?" — máx. 2 reintentos, luego escalación |
| Asegurada sin plan activo (póliza vencida) | "Tu póliza está vencida. Comunícate con NexHealth para renovarla." — sin respuesta de cobertura |
| Respuesta es "no cubierto" | Mostrar resultado negativo en lenguaje empático + opción "¿Quieres explorar otras alternativas?" (US-05 — Could) |
| Sesión expirada durante la consulta | Redirigir a login, retomar contexto de consulta si el token lo permite |

---

## 6. Requerimientos técnicos

### APIs y servicios

| Servicio | Uso | Notas |
|---------|-----|-------|
| Coverage API (legacy) | Consultar cobertura por código de procedimiento + plan del asegurado | REST, ~2s latencia, schema complejo. Sebastián Moya (Tech Lead) es el owner. |
| Vocabulary Mapping Layer | Mapear lenguaje coloquial → código de procedimiento del catálogo | Puede ser tabla de lookup + fuzzy matching en primera iteración. Evaluar si el LLM puede resolver esto también. |
| LLM (a definir: Claude / GPT-4o / Gemini) | Generar respuesta conversacional con los datos de cobertura | Prompt incluye: datos del plan, resultado de Coverage API, vocabulario del usuario. Requiere evaluación de alucinaciones en staging. |
| Feature Flag Service | Toggle para A/B test (respuesta actual vs. conversacional) | PostHog feature flags (ya en el stack de NexHealth). |
| Analytics / Experiment Tracking | Registro de variante, NPS, eventos de CTA, llamadas post-consulta | PostHog Events. Coordinación con Paula Castillo (Data Analyst). |

### Datos requeridos

| Dato | Fuente | Formato |
|------|--------|---------|
| ID del plan del asegurado | Auth token / sesión activa | String (ej: "digital-plus-cl") |
| Resultado de cobertura | Coverage API response | JSON: `{covered: bool, copay: number, conditions: string[]}` |
| Confidence score del LLM | Output del modelo | Float 0–1 |
| Vocabulario coloquial → código de procedimiento | Vocabulary Mapping Layer | Lookup table o embedding |

### Consideraciones de performance

- **Latencia target total:** < 4 segundos (legacy API ~2s + LLM ~1-2s)
- Si la latencia excede 4s en staging, evaluar: streaming de respuesta LLM + spinner informativo con mensaje de contexto ("Consultando tu cobertura...")
- **Umbral de confidence para escalación:** definir en Sprint 01 con Sebastián. Propuesta inicial: < 0.75

### Feature flags

- `coverwise_conversational_response`: boolean — activa la nueva respuesta para el segmento de A/B test
- Estrategia inicial: 50% Plan Digital Plus Chile (segmento de mayor volumen). Rollout gradual por país si el resultado es positivo.
- Flag owner: Sebastián Moya (Tech Lead)

---

## 7. Diseño visual

### Componentes del Design System aplicados

_(Sin design system activo en este ciclo — usar como referencia el template en `contexto/design-system/template-examples/`.)_

- **Card de respuesta:** Container con borde coloreado según resultado (verde: cubierto, rojo: no cubierto, amarillo: incertidumbre)
- **Pill de plan + certeza:** Componente badge pequeño debajo de la respuesta. Texto: "[Nombre del plan] · [Alta / Media] certeza"
- **CTA siguiente paso:** Botón secundario al pie de la card de respuesta. Una sola acción sugerida según el resultado.
- **Banner de advertencia (certeza baja):** Reemplaza la card de respuesta. Icono ⚠ + texto + CTA de escalación.

### Disclaimer regulatorio

Texto fijo al pie de toda respuesta de cobertura:

> *"Esta información es orientativa basada en tu plan contratado y no reemplaza la resolución formal de NexHealth. Para dudas específicas, consulta con un asesor."*

El disclaimer no es modal ni bloqueante. Es texto pequeño, siempre visible, no colapsable.

---

## 8. Acceptance Criteria

### PBI-01 — Conversational Response Engine

```gherkin
Scenario: Respuesta conversacional para procedimiento cubierto
  Given que la asegurada está autenticada con Plan Digital Plus
  And consulta "¿me cubren la resonancia de rodilla?"
  When Coverwise procesa la consulta
  Then la respuesta es en lenguaje coloquial sin términos técnicos de póliza
  And menciona el copago específico en pesos
  And el tiempo total de respuesta es < 4 segundos

Scenario: Respuesta para procedimiento no cubierto
  Given que la asegurada consulta por un procedimiento no cubierto en su plan
  When Coverwise procesa la consulta
  Then la respuesta indica claramente "No está cubierto" en lenguaje empático
  And no muestra texto de póliza crudo

Scenario: API legacy no responde (timeout)
  Given que la Coverage API no responde en > 3 segundos
  When el timeout se dispara
  Then Coverwise muestra un mensaje de error amigable
  And ofrece la opción de conectar con un asesor
  And no muestra respuesta de cobertura parcial ni inventada
```

### PBI-02 — Plan & Confidence Indicator

```gherkin
Scenario: Indicador de plan en respuesta de alta certeza
  Given que la respuesta LLM tiene confidence score >= 0.75
  When la respuesta se muestra al asegurado
  Then aparece el pill "[Nombre del plan] · Alta certeza" debajo de la respuesta

Scenario: Indicador de certeza media
  Given que la respuesta LLM tiene confidence score entre 0.50 y 0.74
  When la respuesta se muestra
  Then el pill muestra "· Certeza media"
  And aparece texto adicional: "Si tienes dudas, un asesor puede confirmar."
```

### PBI-03 — Suggested Next Step

```gherkin
Scenario: CTA de siguiente paso para resultado cubierto
  Given que la respuesta es "cubierto"
  When el asegurado ve la respuesta
  Then aparece un CTA "¿Te ayudo a encontrar un prestador?" al pie de la card

Scenario: CTA de siguiente paso para resultado no cubierto
  Given que la respuesta es "no cubierto"
  When el asegurado ve la respuesta
  Then aparece un CTA "¿Quieres explorar otras alternativas?" al pie de la card
```

### PBI-04 — Smart Escalation Fallback

```gherkin
Scenario: Escalación cuando confidence < umbral
  Given que el LLM devuelve confidence score < 0.50
  When Coverwise genera la respuesta
  Then muestra la card de advertencia (no la card de respuesta normal)
  And ofrece conectar con un asesor con el payload de contexto preparado
  And al conectar, el asesor recibe: consulta original, plan, y respuesta tentativa del LLM

Scenario: Escalación cuando el procedimiento no existe en catálogo
  Given que el Vocabulary Mapping Layer no encuentra el procedimiento tras 2 reintentos
  When se agota el tercer intento
  Then Coverwise ofrece escalación inteligente con el texto de la consulta preservado
```

### PBI-05 — A/B Test Infrastructure

```gherkin
Scenario: Asignación a variante del experimento
  Given que el asegurado tiene el feature flag coverwise_conversational_response
  When abre Coverwise y formula una consulta
  Then recibe la respuesta conversacional (variante)
  And el evento "coverwise_response_shown" se registra en PostHog con {variant: "conversational"}

Scenario: Tracking de CTA del siguiente paso
  Given que el asegurado recibe la respuesta conversacional
  When hace clic en el CTA de siguiente paso
  Then el evento "coverwise_next_step_clicked" se registra en PostHog con {variant, result_type, cta_label}
```

---

## 9. Plan de rollout

| Fase | Alcance | Criterio de avance |
|------|---------|-------------------|
| 1. Staging | Equipo interno NexHealth | Validación técnica: LLM sin alucinaciones en muestra de 50 casos reales. Aprobación compliance del disclaimer. |
| 2. A/B test en producción | 50% Plan Digital Plus Chile | NPS post-consulta ≥ +5 puntos ó reducción de llamadas ≥ 20% en 14 días de datos |
| 3. Full rollout | 100% usuarios activos | Si criterio de A/B cumplido. Rollout por país: Chile → Colombia → México |

---

## 10. Dependencias y riesgos

| Dependencia / Riesgo | Owner | Status | Mitigación |
|----------------------|-------|--------|------------|
| Acceso a Coverage API del sistema legacy | Sebastián Moya | Confirmar en Sprint 01 | Prototipo con datos mock en staging para no bloquear desarrollo LLM |
| Aprobación de disclaimer por equipo de compliance | Andrés Donoso (VP Ops) | Iniciar semana 1 | Borrador del disclaimer ya incluido en este PRD para revisión anticipada |
| Selección del LLM proveedor | Sebastián Moya + Tríada | Decisión en Sprint 01 | Evaluar Claude API vs. GPT-4o en función de latencia y precisión de cobertura con el schema del legacy |
| Implementación de NPS in-app (si no existe) | Paula Castillo | Confirmar existencia | Si no existe, priorizar implementación en Sprint 01 para tener baseline del control |
| Tasa de respuesta NPS < 10% | Paula Castillo | Riesgo identificado | Diseñar el prompt NPS in-app para maximizar respuesta (timing, longitud, contexto) |

---

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 0.1 | 2026-05-06 | Claude (Handoff facilitador) | Draft inicial. Cubre PBIs 01–05. User flow completo incluyendo certeza baja. Acceptance criteria en Gherkin. Plan de rollout en 3 fases. |
