# ADR-NNNN: [Decisión corta y clara]

> Plantilla de Architecture Decision Record. Copiar como `NNNN-titulo-decision.md` con el siguiente número global consecutivo.
>
> Reglas:
> - Una decisión por ADR. Documenta decisiones, no diseños detallados.
> - Un ADR **aceptado es inmutable**: no se edita. Si la decisión cambia, se crea un ADR nuevo que lo *supersede* y en el anterior solo se actualiza el estado a «Superado por ADR-XXXX».
> - Un ADR superado se marca, nunca se borra.
> - Granularidad: decisiones costosas de revertir (stack, arquitectura, base de datos, estilo de API, autenticación, despliegue, build vs buy).
> - No inventar alternativas: si no se evaluaron alternativas, se indica «No documentadas».

| Campo | Valor |
| --- | --- |
| Número | ADR-NNNN |
| Estado | Propuesto / Aceptado / Superado por ADR-XXXX / Obsoleto |
| Fecha | AAAA-MM-DD |
| Fuentes | Documentos o evidencias que respaldan la decisión |
| Supersede a | ADR-XXXX (si aplica) |

## 1. Contexto

Fuerzas técnicas y de negocio, restricciones, atributos de calidad y problema que motiva la decisión. Cada afirmación debe citar su fuente.

## 2. Decisión

Qué se decide, en una o dos frases claras.

## 3. Alternativas consideradas

| Alternativa | Motivo por el que no se eligió |
| --- | --- |
| … | … |

## 4. Consecuencias

**Positivas**
- …

**Negativas / trade-offs**
- …

**Riesgos y pendientes**
- …

## 5. Enlaces y referencias

- Specs relacionadas: …
- ADR relacionados: …
- Fuentes: …
