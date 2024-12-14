# Next.js Project Improvements

Este proyecto incluye diversas mejoras utilizando GitHub Actions para automatizar tareas clave en el desarrollo y mantenimiento del código.

## Introducción: ¿Qué son las GitHub Actions?

GitHub Actions es una plataforma que permite automatizar flujos de trabajo directamente desde los repositorios de GitHub. Proporciona una manera sencilla de crear, gestionar y ejecutar procesos automatizados (llamados workflows) como tests, despliegues, o la generación de métricas. Los workflows son definidos mediante archivos YAML y se ejecutan en respuesta a eventos como un push, una pull request o un cron job.

## Workflows Configurados

En este proyecto hemos configurado varios workflows con los siguientes jobs:

### `linter_job`

- **Descripción**: Ejecuta un linter para verificar que la sintaxis del código JavaScript es correcta.
- **Beneficios**: Ayuda a mantener un estándar de calidad en el código.

### `cypress_job`

- **Descripción**: Ejecuta tests end-to-end con Cypress para validar el comportamiento de la aplicación.
- **Beneficios**: Garantiza que las funcionalidades del proyecto funcionan según lo esperado.

### `add_badge_job`

- **Descripción**: Actualiza el archivo README.md con un badge que indica si los tests de Cypress se ejecutaron correctamente o no.

### `deploy_job`

- **Descripción**: Publica automáticamente la aplicación en la plataforma Vercel tras un push exitoso.

  ### `notification_job`

- **Descripción**: Nos envía una notificación a Telegram con el resultado de la ejecución de nuestro workflow.

### `metrics_job`

- **Descripción**: Genera un panel con métricas de los lenguajes más utilizados en tu perfil de GitHub.
- **Beneficios**: Actualiza automáticamente el README para incluir estas métricas.

## Pasos Realizados

### 1. Configuración de Métricas

- Se utilizó la acción `Metrics Embed` para generar las métricas.
- Un token personal (`METRICS_TOKEN`) fue configurado en los Secrets del repositorio con permisos para acceder a la API de GitHub.
- Se añadió un job llamado `metrics_job` que ejecuta la acción y actualiza el archivo README.md con las métricas generadas.

### 2. Integración con Telegram

- Se creó un job `notification_job` que envía notificaciones sobre el estado del workflow a un chat de Telegram.
- Utiliza los secretos `TELEGRAM_TOKEN` y `TELEGRAM_CHAT_ID` para conectarse a la API de Telegram y enviar el mensaje con los resultados de los jobs.

### 3. Actualización Automática del README

- Tanto el `add_badge_job` como el `metrics_job` actualizan dinámicamente el README.md para mostrar información relevante sobre los resultados de los tests y las métricas del perfil.

## Resultados de Métricas

![Metrics](https://metrics.lecoq.io/username)

## Conceptos Tratados

### Workflows y Jobs

- **Workflow**: Un workflow es una serie de procesos automatizados. Cada workflow puede contener uno o más jobs, que se ejecutan de manera secuencial o paralela.
- **Job**: Un job es una unidad de trabajo dentro de un workflow. Cada job puede contener uno o más pasos que se ejecutan en un entorno específico.

### GitHub Actions

- **Acciones**: Reutilización de acciones existentes como `actions/checkout`, `cypress-io/github-action`, y `lowlighter/metrics`.
- **Jobs Personalizados**: Creación de jobs personalizados para tareas específicas como despliegues en Vercel y notificaciones en Telegram.

### Automatización del README

- **Actualización Dinámica**: Uso de workflows para mantener el archivo README.md siempre actualizado con información relevante sobre los resultados de los tests y las métricas del perfil.
