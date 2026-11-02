
# Automation 2 — Imperio Tickets

## Sobre el proyecto

Imperio Tickets es una plataforma de venta online de entradas para eventos, en la que participo como cofundador.

Para este proyecto de Automation IA Avanzado, decidí trabajar sobre una necesidad real de la plataforma: mejorar la gestión de consultas de compradores y productores mediante inteligencia artificial.

## Módulo 1 — Agente de atención inicial

En esta primera etapa desarrollé un agente en n8n que recibe consultas a través de un chat, las interpreta y decide cómo responder.

El agente puede resolver preguntas generales y, cuando detecta un problema o una solicitud que necesita seguimiento, utiliza Google Sheets para registrar la consulta y derivarla a revisión humana.

También integré Gmail para recibir un registro de cada ejecución y poder supervisar su funcionamiento.

Realicé pruebas con consultas sobre entradas QR y solicitudes comerciales de productores, comprobando que el agente registra correctamente los casos que necesitan atención.

## Herramientas utilizadas

n8n · Docker · Groq · Google Sheets · Gmail

## Entregable

**Módulo 1:** `checkpoint1_leonardo_riera.json`

El archivo contiene el workflow desarrollado y exportado desde n8n.
