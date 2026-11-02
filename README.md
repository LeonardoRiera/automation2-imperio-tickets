
# Automation 2 — Imperio Tickets

## Descripción del proyecto

Imperio Tickets es una plataforma de venta online de entradas para eventos que atiende consultas de compradores y productores.

Este proyecto busca automatizar la atención inicial mediante un sistema de agentes de inteligencia artificial, capaz de interpretar consultas, brindar respuestas y utilizar herramientas externas cuando una situación requiere seguimiento humano.

El sistema está desarrollado en **n8n** y evolucionará progresivamente durante los módulos del curso.

---

## Módulo 1 — Agente autónomo básico

### Objetivo

Implementar un agente de IA funcional que reciba consultas en lenguaje natural, identifique las necesidades del usuario y decida autónomamente cuándo utilizar una herramienta externa.

### Arquitectura implementada

**Flujo principal:**

`Chat Trigger → AI Agent → Gmail`

**Conexiones del AI Agent:**

- **Groq Chat Model:** modelo de lenguaje `openai/gpt-oss-20b`.
- **Google Sheets Tool:** herramienta para registrar consultas que requieren seguimiento o revisión humana.

### Funcionamiento

El agente recibe una consulta desde el chat de n8n y determina cómo proceder.

**1. Consultas informativas**

Cuando puede responder con la información disponible, genera una respuesta directamente, sin utilizar Google Sheets.

**2. Consultas que requieren seguimiento**

Cuando identifica problemas con pagos, entradas QR, acceso a eventos, reclamos o solicitudes comerciales de productores, utiliza Google Sheets para registrar el caso.

Cada registro incluye:

- Fecha de la consulta.
- Mensaje recibido.
- Tipo de usuario.
- Categoría.
- Necesidad de revisión humana.

**3. Observabilidad**

Al finalizar la ejecución, Gmail envía un correo interno con la consulta original y la respuesta del agente.

### Configuración del agente

El agente utiliza un **System Prompt modular**, organizado en las siguientes secciones:

- **Role:** identidad y función del agente.
- **Scope:** ámbito de consultas permitido.
- **Objective:** resultados esperados.
- **Rules:** restricciones y comportamiento.
- **Escalation:** criterios para registrar y derivar consultas.

Se configuró un máximo de **7 iteraciones** para controlar la ejecución.

La herramienta Google Sheets cuenta con una descripción semántica que indica cuándo debe utilizarse y cuándo no.

---

## Pruebas y validación

Se realizaron pruebas funcionales con diferentes escenarios:

| Escenario | Comportamiento esperado | Resultado |
|---|---|---|
| Problema con recepción de entradas QR | Registrar consulta y solicitar revisión humana | Correcto |
| Consulta comercial de un productor | Identificar al productor y registrar la solicitud | Correcto |

Se verificó que el agente ejecuta la herramienta Google Sheets cuando corresponde y que Gmail genera el reporte interno de ejecución.

---

## Tecnologías utilizadas

- **n8n:** diseño y ejecución del workflow.
- **Docker:** ejecución local de n8n.
- **Groq:** proveedor del modelo de lenguaje.
- **Google Sheets:** registro estructurado de consultas.
- **Gmail:** observabilidad mediante notificaciones internas.
- **Google Cloud OAuth2:** autenticación de los servicios de Google.

---

## Entregable

**Archivo:** `checkpoint1_leonardo_riera.json`

Contiene el workflow exportado de n8n correspondiente al Módulo 1.

Para utilizarlo en otra instancia de n8n, es necesario importar el archivo y configurar las credenciales y los servicios externos correspondientes.

---

## Próximos pasos

El proyecto continuará desarrollándose en los siguientes módulos, incorporando nuevas capacidades de orquestación, especialización de agentes y automatización de procesos para Imperio Tickets.
