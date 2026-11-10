# Módulo 4 — Integraciones Avanzadas

**Proyecto:** Imperio Tickets  
**Autor:** Leonardo Riera

## Descripción

Automatización desarrollada en n8n para gestionar consultas de compradores y productores mediante agentes de IA e integraciones externas.

El workflow incorpora:

- **Gmail:** recepción de consultas y creación de borradores.
- **HubSpot:** búsqueda y gestión de contactos sin duplicados.
- **Airtable:** memoria persistente de conversaciones.
- **Groq:** clasificación y procesamiento mediante IA.
- **Telegram:** notificaciones operativas.

## Controles implementados

Filtrado de correos automáticos, validación de emails y prevención de bucles.

Las respuestas se guardan como borradores de Gmail para **revisión humana antes del envío (HITL)**.

## Entregables

- `checkpoint4_leonardo_riera.json` — Workflow de n8n.
- `evidencias/` — Capturas de las pruebas funcionales.

**Nota:** Para ejecutar el workflow se requieren credenciales propias y los subworkflows de Compradores y Productores.

