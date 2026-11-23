# 2. Arquitectura unificada del sistema AGI
Resultado de contrastar la propuesta de la otra IA (10 agentes) con la propuesta de Claude (cadena automática con orquestador). Se aplica **del Video 02 en adelante**.

## Flujo
```
                 AGI-00 ORQUESTADOR (coordina, reintenta, registra estado)
                                  │
AGI-01 Director Académico → AGI-02 Investigador → AGI-03 Diseñador Pedagógico
   → AGI-04 Guionista → AGI-05 Revisor Técnico ──✗──► vuelve al Guionista (máx. 3 veces)
                                  │ ✓
                 👤 APROBACIÓN HUMANA JJC (por WhatsApp)
                                  │
        AGI-07 Narrador  +  AGI-06 Generador Visual  (en paralelo)
                                  │
        AGI-08 Editor Audiovisual (+ subtítulos, −14 LUFS)
                                  │
        🔍 CONTROL DE CALIDAD automático
                                  │
        AGI-09 Publicador YouTube → AGI-10 Analista ──► vuelve a AGI-01
```

## Agentes: qué reciben y qué entregan
| Agente | Recibe | Entrega |
|---|---|---|
| 00 Orquestador | Listado maestro y estado de cada lección | Ejecuta la cadena, registra errores |
| 01 Director Académico | Listado maestro + métricas | Próxima lección y objetivos (**sin salirse del listado maestro**) |
| 02 Investigador | Tema | Ficha técnica con **fuentes citadas** (normas, manuales, libros) |
| 03 Diseñador Pedagógico | Ficha técnica | Objetivos, ejemplo, caso real, secuencia de conceptos |
| 04 Guionista | Diseño de la clase | `guion.json` por escenas, estilo del Video 01, ≤ 10 min |
| 05 Revisor Técnico | Guion, imágenes y fuentes | Aprobado / rechazado con lista de errores (incluye seguridad en imágenes) |
| 👤 JJC | Guion aprobado | ✓ Aprobar / ✎ Corregir / ✗ Descartar |
| 06 Generador Visual | Escenas | Gráficos de concepto, imágenes de planta, animaciones |
| 07 Narrador | Narración | Voz con marcas de tiempo |
| 08 Editor | Voz, avatar, imágenes, música | Video final + subtítulos .srt |
| 🔍 Control de Calidad | Video final | Pasa / falla (duración, audio, planos repetidos, subtítulos) |
| 09 Publicador | Video y guion | Título, descripción, capítulos, miniatura, publicación programada |
| 10 Analista | Datos de YouTube | Informe semanal y recomendaciones |

## Aprobación humana (por WhatsApp)
1. El Revisor Técnico aprueba → el Orquestador se **pausa**.
2. JJC recibe: resumen (objetivos, fuentes, puntos de seguridad), guion completo en PDF y observaciones del Revisor.
3. Botones: **✓ APROBADO** (sigue la producción) · **✎ CORREGIR** (vuelve al Guionista) · **✗ DESCARTAR** (vuelve al Director).
4. **Sin respuesta, no se produce nada.** Nunca se publica sin el ✓ de JJC.
5. Se registra qué se aprobó, cuándo y con qué cambios; el Analista aprende de las correcciones.

Requisitos: API oficial de WhatsApp Business (Meta o Twilio), número dedicado (no el personal), cuenta Meta Business verificada.

## Descartado de la primera propuesta de Claude
- Temario nuevo de ~60 videos → **descartado** (manda el listado maestro).
- Plantilla con quiz y "gancho de falla" → **descartada** (la referencia de estilo es el Video 01).
