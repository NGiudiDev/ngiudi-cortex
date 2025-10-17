# Tipologías de Requisitos

## Introducción

Los requisitos son la base fundamental de cualquier proyecto de software. Representan las necesidades, expectativas y restricciones que debe satisfacer el sistema. Una correcta clasificación y comprensión de los diferentes tipos de requisitos es crucial para el éxito del proyecto, ya que determina qué se va a construir, cómo debe comportarse y bajo qué condiciones debe operar.

## Clasificación Principal de Requisitos

### Requisitos Funcionales

**Definición**: Especifican qué debe hacer el sistema, describiendo las funciones, servicios y capacidades que debe proporcionar.

**Características**:
- Describen comportamientos específicos del sistema
- Son medibles y verificables
- Definen entradas, procesamiento y salidas
- Especifican interacciones con usuarios y sistemas externos

**Ejemplos**:
- "El sistema debe permitir al usuario iniciar sesión con email y contraseña"
- "El sistema debe generar reportes en formato PDF"
- "La aplicación debe enviar notificaciones push cuando llegue un nuevo mensaje"
- "El sistema debe calcular automáticamente los impuestos según la ubicación del usuario"

**Técnicas de especificación**:
- Casos de uso
- Historias de usuario
- Especificaciones formales
- Diagramas de flujo

### Requisitos No Funcionales

**Definición**: Especifican cómo debe comportarse el sistema, definiendo criterios de calidad y restricciones operacionales.

**Importancia**: A menudo son más críticos que los funcionales para el éxito del proyecto, ya que afectan la experiencia del usuario y la viabilidad técnica.

#### Subcategorías de Requisitos No Funcionales

##### Requisitos de Rendimiento
- **Tiempo de respuesta**: "Las consultas a la base de datos deben ejecutarse en menos de 2 segundos"
- **Throughput**: "El sistema debe procesar al menos 1000 transacciones por minuto"
- **Capacidad**: "La aplicación debe soportar 10,000 usuarios concurrentes"
- **Escalabilidad**: "El sistema debe poder aumentar su capacidad en un 200% sin rediseño"

##### Requisitos de Seguridad
- **Autenticación**: "Todos los usuarios deben autenticarse mediante 2FA"
- **Autorización**: "Solo administradores pueden acceder al panel de control"
- **Encriptación**: "Todos los datos sensibles deben encriptarse con AES-256"
- **Auditoría**: "El sistema debe registrar todas las acciones de los usuarios"

##### Requisitos de Usabilidad
- **Facilidad de uso**: "Un usuario nuevo debe poder completar su primera tarea en menos de 5 minutos"
- **Accesibilidad**: "La interfaz debe cumplir con las pautas WCAG 2.1 AA"
- **Responsividad**: "La aplicación debe funcionar correctamente en dispositivos móviles"
- **Internacionalización**: "El sistema debe soportar múltiples idiomas"

##### Requisitos de Confiabilidad
- **Disponibilidad**: "El sistema debe tener un uptime del 99.9%"
- **Tolerancia a fallos**: "El sistema debe continuar funcionando si un componente falla"
- **Recuperación**: "El sistema debe recuperarse automáticamente en menos de 5 minutos tras una falla"
- **Precisión**: "Los cálculos financieros deben ser exactos hasta 2 decimales"

##### Requisitos de Mantenibilidad
- **Modificabilidad**: "Agregar una nueva función debe tomar máximo 2 días de desarrollo"
- **Testabilidad**: "El código debe tener al menos 80% de cobertura de pruebas"
- **Documentación**: "Todas las APIs deben estar documentadas con OpenAPI"
- **Modularidad**: "El sistema debe permitir actualizaciones independientes de módulos"

##### Requisitos de Portabilidad
- **Compatibilidad**: "La aplicación debe funcionar en Windows, macOS y Linux"
- **Migración**: "Los datos deben poder migrarse a otro sistema en menos de 4 horas"
- **Estándares**: "El sistema debe usar formatos de datos estándar (JSON, XML)"

## Clasificación por Origen

### Requisitos del Usuario
**Fuente**: Usuarios finales, clientes, stakeholders del negocio
**Características**: 
- Expresados en lenguaje natural
- Enfocados en objetivos de negocio
- Pueden ser ambiguos o incompletos

**Ejemplo**: "Quiero poder ver mis ventas del mes anterior"

### Requisitos del Sistema
**Fuente**: Análisis técnico de los requisitos del usuario
**Características**:
- Más detallados y precisos
- Especificaciones técnicas claras
- Verificables y medibles

**Ejemplo**: "El módulo de reportes debe consultar la tabla 'ventas' filtrando por fecha >= primer día del mes anterior AND fecha <= último día del mes anterior"

### Requisitos de Negocio
**Fuente**: Objetivos estratégicos de la organización
**Características**:
- Alto nivel, orientados a objetivos
- Justifican la existencia del proyecto
- Definen el valor esperado

**Ejemplo**: "Reducir el tiempo de procesamiento de órdenes en un 50% para mejorar la satisfacción del cliente"

## Clasificación por Prioridad

### Método MoSCoW
- **Must Have**: Críticos para el éxito del proyecto
- **Should Have**: Importantes pero no críticos
- **Could Have**: Deseables si hay tiempo y recursos
- **Won't Have**: Fuera del alcance actual

### Método de Kano
- **Básicos**: Esperados por el usuario (causan insatisfacción si faltan)
- **De rendimiento**: Satisfacción proporcional a su calidad
- **Emocionantes**: Sorprenden positivamente al usuario

## Técnicas de Elicitación por Tipo de Requisito

### Para Requisitos Funcionales
- **Entrevistas**: Conversaciones estructuradas con stakeholders
- **Observación**: Análisis de procesos actuales
- **Casos de uso**: Scenarios de interacción
- **Prototipos**: Demostraciones tempranas

### Para Requisitos No Funcionales
- **Benchmarking**: Comparación con sistemas similares
- **Análisis de SLA**: Revisión de acuerdos de servicio
- **Pruebas de concepto**: Validación de viabilidad técnica
- **Métricas históricas**: Datos de sistemas existentes

## Gestión de Requisitos

### Trazabilidad
- **Forward tracing**: De requisitos a diseño e implementación
- **Backward tracing**: De código/pruebas a requisitos originales
- **Bidirectional**: Seguimiento en ambas direcciones

### Control de Cambios
1. **Solicitud de cambio**: Documentación formal del cambio
2. **Análisis de impacto**: Evaluación de efectos en el proyecto
3. **Aprobación**: Decisión de stakeholders autorizados
4. **Implementación**: Actualización de documentos y sistema
5. **Verificación**: Confirmación de que el cambio es correcto

### Herramientas de Gestión
- **JIRA**: Gestión de requisitos y seguimiento
- **Confluence**: Documentación colaborativa
- **Trello**: Gestión visual simple
- **Azure DevOps**: Integración completa con desarrollo
- **Requirements tools**: IBM DOORS, Polarion

## Problemas Comunes y Soluciones

### Requisitos Ambiguos
**Problema**: Interpretaciones múltiples o vagas
**Solución**: 
- Usar lenguaje preciso y específico
- Incluir ejemplos y contraejemplos
- Revisiones con stakeholders

### Requisitos Conflictivos
**Problema**: Requisitos que se contradicen entre sí
**Solución**:
- Matriz de trazabilidad
- Sesiones de resolución con stakeholders
- Priorización clara

### Scope Creep
**Problema**: Adición constante de nuevos requisitos
**Solución**:
- Control de cambios formal
- Comunicación clara del impacto
- Gestión de expectativas

### Requisitos No Verificables
**Problema**: Imposibilidad de comprobar si se cumple el requisito
**Solución**:
- Criterios de aceptación específicos
- Métricas cuantificables
- Métodos de prueba definidos

## Mejores Prácticas

### Durante la Elicitación
1. **Involucrar a todos los stakeholders** relevantes
2. **Usar múltiples técnicas** de elicitación
3. **Documentar inmediatamente** las decisiones
4. **Validar comprensión** mediante prototipos o ejemplos

### Durante la Especificación
1. **Escribir de forma clara y concisa**
2. **Usar estándares y plantillas**
3. **Incluir criterios de aceptación**
4. **Revisar y validar** con stakeholders

### Durante la Gestión
1. **Mantener trazabilidad** completa
2. **Controlar cambios** formalmente
3. **Comunicar impactos** claramente
4. **Actualizar documentación** consistentemente