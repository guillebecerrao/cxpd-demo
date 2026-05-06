---
title: Registro de Ideas — C1.1 — Ciclo 01/2026
oportunidad: "C1.1 — El asegurado recibe una respuesta de Coverwise pero no le genera suficiente claridad ni confianza para actuar sin llamar"
author: Claude (Shape/I&V facilitador)
created: 2026-05-06
last_modified: 2026-05-06
last_modified_by: Claude (Shape/I&V facilitador)
version: 1.0
modification_count: 1
status: in_progress
cycle: ciclo-01-2026
---

# Registro de Ideas — C1.1

> **Oportunidad target:** C1.1 — La respuesta de Coverwise no genera claridad ni confianza suficiente para actuar sin llamar.
>
> **Metodología:** Ideación divergente antes de convergir. Todas las ideas se registran sin filtro inicial.
> Referencia: Torres, *Continuous Discovery Habits*, Cap. 10.

---

## Ideas generadas

### Idea 1 — Respuesta conversacional generada por LLM

**Descripción:** En vez de devolver el texto literal de la póliza, Coverwise usa un LLM para generar una respuesta en lenguaje coloquial, específica al plan del asegurado, con una confirmación clara ("Sí, está cubierto" / "No está cubierto").

**Cómo ataca C1.1:** Elimina el lenguaje técnico de la póliza como barrera. La respuesta se adapta al vocabulario del usuario, no al de la cobertura.

**Ejemplo:** En vez de "El artículo 5.3.2 de tu plan contempla cobertura parcial para intervenciones ambulatorias de clase B", el usuario ve: "Sí, tu consulta de traumatología está cubierta. Pagas solo el copago de $12.000."

---

### Idea 2 — Indicador de certeza + plan explícito

**Descripción:** Cada respuesta incluye dos elementos adicionales: (a) el nivel de certeza ("Alta confianza — basado en tu Plan Digital Plus") y (b) la indicación de que la respuesta aplica específicamente a su contrato, no es genérica.

**Cómo ataca C1.1:** Responde directamente al supuesto C-02 (lenguaje técnico) y C-03 (¿aplica a mi plan?). El usuario sabe que la respuesta es suya, no de otro plan.

**Ejemplo:** Una pastilla verde arriba de la respuesta: "✓ Aplicado a tu plan: Digital Plus | Certeza: Alta"

---

### Idea 3 — Respuesta con ejemplo concreto + siguiente paso

**Descripción:** Post-respuesta, el sistema agrega una oración de traducción práctica y una acción sugerida. El formato es: respuesta → qué significa → qué puedes hacer ahora.

**Cómo ataca C1.1:** La brecha de confianza no es solo entender la respuesta — es saber qué hacer con ella. El siguiente paso cierra el loop del journey.

**Ejemplo:** "Sí, está cubierto. Esto significa que puedes ir a cualquier prestador de nuestra red sin trámite previo. ¿Te ayudo a encontrar uno cerca tuyo?"

---

### Idea 4 — Escalación inteligente con contexto preservado

**Descripción:** Cuando la consulta es ambigua o la certeza es baja, Coverwise no falla silenciosamente ni dice "no entiendo". En cambio, ofrece conectar con un asesor y le pasa el contexto armado: nombre del procedimiento, plan, y la respuesta tentativa. El asesor toma la conversación sin empezar de cero.

**Cómo ataca C1.1:** Para los casos donde el LLM no puede dar certeza alta, la escalación inteligente transforma el "no confío" en "sé que hay un humano que puede confirmarme esto". Reduce la llamada frustrada y la convierte en una llamada corta y con contexto.

**Ejemplo:** "No estoy 100% seguro para tu caso específico. ¿Quieres que un asesor lo confirme ahora? Ya tiene todo el contexto de tu consulta."

---

### Idea 5 — Respuesta dual: resumen simple + detalle técnico bajo demanda

**Descripción:** La respuesta principal es corta y en lenguaje coloquial. Un CTA secundario "Ver detalle de tu póliza" despliega el texto exacto del contrato para usuarios que necesitan la fuente formal (ej: para presentar en la clínica o ante seguros complementarios).

**Cómo ataca C1.1:** Sirve a dos perfiles: el usuario que confía con el resumen simple, y el usuario que necesita el texto técnico para validar. No obliga al primer perfil a leer lo que confunde al segundo.

---

## Ideas descartadas en sesión

| Idea | Razón de descarte |
|------|------------------|
| Chatbot con avatar visual | No ataca el problema de confianza en la información — es cosmético |
| Encuesta de satisfacción post-respuesta | Útil para métricas, pero no resuelve la oportunidad para el usuario actual |
| FAQ de coberturas frecuentes | Estático, no conversa, no personaliza — regresa al problema actual |

---

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | 2026-05-06 | Claude (I&V facilitador) | 5 ideas generadas sobre C1.1. 3 ideas descartadas en sesión. |
