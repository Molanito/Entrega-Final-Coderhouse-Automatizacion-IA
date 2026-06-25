# Entrega Final – Ecosistema de Automatización IA Autónomo para Negocios

## Autor

Juan Fernando Verú Molano

## Curso

Coderhouse – Automatización e Inteligencia Artificial

## Descripción del Proyecto

Este proyecto implementa un ecosistema de automatización inteligente para la generación y aprobación de contenido para redes sociales.

El sistema integra n8n como orquestador principal, Airtable como base de datos y memoria, OpenAI GPT-4o para la generación de contenido y Gmail como canal de comunicación y validación humana.

## Tecnologías Utilizadas

* n8n
* Airtable
* OpenAI GPT-4o
* Gmail

## Arquitectura General

Airtable → n8n → OpenAI → Gmail → Human In The Loop → Resultado Final

## Flujo de Trabajo

1. Lectura de registros pendientes desde Airtable.
2. Validación de datos obligatorios.
3. Generación de contenido mediante GPT-4o.
4. Almacenamiento del contenido generado.
5. Envío de correo de aprobación.
6. Espera de validación humana (HITL).
7. Aprobación o rechazo.
8. Actualización de estados.
9. Notificación final.

## Human In The Loop (HITL)

El sistema incorpora una validación humana antes de ejecutar acciones críticas. El contenido generado es enviado por correo electrónico para revisión y aprobación antes de continuar con el proceso.

## Gestión de Errores

Se implementó una ruta de manejo de errores para registrar:

* Datos incompletos.
* Errores de integración.
* Fallos del modelo de IA.
* Problemas de comunicación.

Todos los errores son almacenados en Airtable para seguimiento y auditoría.

## Archivos Incluidos

* Entrega_Final.pdf
* Coderhouse_Workflow_Final.json
* Evidencias del funcionamiento
* Diagrama de arquitectura

## Evidencias

El repositorio incluye capturas de:

* Base de datos Airtable.
* Workflow en n8n.
* Nodo Wait (Human In The Loop).
* Correo de aprobación.
* Manejo de errores.
* Ejecución exitosa del flujo.

  ## Base de Datos

Enlace Airtable (Modo Lectura)
https://airtable.com/appRvUqBFFJfMH4JW/shrZeLWtHNmlfzfTg

La base de datos almacena temas de contenido, resultados generados por IA, estados del flujo y registros de errores.

## Trigger Automático

El sistema opera mediante un disparador automático conectado a Airtable.

Cuando se detecta un nuevo registro con estado "Pendiente", el workflow inicia automáticamente el procesamiento sin intervención manual.

## Prevención de Bucles

Para evitar ejecuciones repetidas:

Solo se procesan registros con estado:

* Pendiente

Los estados:

* Procesado IA
* Aprobado Humano
* Rechazado
* Error

son excluidos del procesamiento.

## Estrategia de Resiliencia

El sistema contempla manejo de errores mediante rutas de recuperación y registro automático de incidencias.

Cualquier excepción detectada actualiza Airtable con el estado Error y registra la información correspondiente para auditoría.


## Conclusión

La solución desarrollada demuestra la integración de automatización, inteligencia artificial, almacenamiento de datos y validación humana dentro de un ecosistema empresarial moderno, cumpliendo con los requisitos establecidos para la entrega final.
