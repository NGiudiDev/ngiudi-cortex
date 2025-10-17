# Metodologías para Obtener Requerimientos

## Introducción

La elicitación de requerimientos es una de las fases más críticas en el desarrollo de software. Un buen proceso de obtención de requerimientos puede determinar el éxito o fracaso de un proyecto. Esta disciplina requiere tanto habilidades técnicas como interpersonales, ya que implica entender necesidades complejas, gestionar expectativas y traducir ideas abstractas en especificaciones concretas.

## Fundamentos de la Elicitación

### ¿Por qué es Importante?

- **Reduce riesgos**: Identificar problemas temprano es más barato que corregirlos después
- **Mejora comunicación**: Establece un lenguaje común entre stakeholders
- **Orienta el desarrollo**: Proporciona dirección clara al equipo técnico
- **Gestiona expectativas**: Alinea la visión de todos los involucrados

### Desafíos Comunes

1. **Stakeholders no saben exactamente qué quieren**
2. **Comunicación deficiente entre áreas técnicas y de negocio**
3. **Requisitos cambiantes durante el desarrollo**
4. **Múltiples stakeholders con intereses conflictivos**
5. **Limitaciones de tiempo y presupuesto**

## Metodologías Principales

### 1. Entrevistas

**Descripción**: Conversaciones estructuradas o semi-estructuradas con stakeholders clave.

**Cuándo usar**:
- Al inicio del proyecto para entender el contexto general
- Para obtener información detallada de expertos del dominio
- Cuando se necesita profundizar en temas específicos

**Tipos de entrevistas**:

#### Entrevistas Estructuradas
- **Características**: Preguntas predefinidas, orden fijo
- **Ventajas**: Consistencia, fácil comparación de respuestas
- **Desventajas**: Menos flexibilidad, puede limitar descubrimientos

#### Entrevistas Semi-estructuradas
- **Características**: Guión flexible, permite exploración
- **Ventajas**: Balance entre estructura y flexibilidad
- **Desventajas**: Requiere más habilidad del entrevistador

#### Entrevistas No Estructuradas
- **Características**: Conversación abierta, exploratoria
- **Ventajas**: Máxima flexibilidad, puede revelar necesidades ocultas
- **Desventajas**: Difícil de controlar, resultados inconsistentes

**Mejores prácticas**:
- Preparar preguntas abiertas y cerradas
- Escuchar más que hablar
- Tomar notas y grabar (con permiso)
- Validar entendimiento parafraseando
- Hacer seguimiento por escrito

**Ejemplo de guión de entrevista**:
```
1. Presentación (5 min)
   - Objetivos de la entrevista
   - Confidencialidad y grabación

2. Contexto general (10 min)
   - ¿Cuál es su rol en la organización?
   - ¿Cómo trabaja actualmente?

3. Problemas y necesidades (15 min)
   - ¿Qué problemas enfrenta en su trabajo diario?
   - ¿Qué le gustaría que mejorara?

4. Visión de la solución (15 min)
   - ¿Cómo se imagina la solución ideal?
   - ¿Qué funcionalidades son más importantes?

5. Restricciones y criterios (10 min)
   - ¿Qué limitaciones debemos considerar?
   - ¿Cómo mediríamos el éxito?

6. Cierre (5 min)
   - Próximos pasos
   - Disponibilidad para seguimiento
```

### 2. Observación

**Descripción**: Análisis directo de cómo los usuarios realizan sus tareas actualmente.

**Tipos de observación**:

#### Observación Pasiva
- **Proceso**: El analista observa sin interferir
- **Ventajas**: Comportamiento natural, no influye en el proceso
- **Desventajas**: No se pueden hacer preguntas en tiempo real

#### Observación Activa
- **Proceso**: El analista hace preguntas durante la observación
- **Ventajas**: Clarificación inmediata, mejor comprensión
- **Desventajas**: Puede alterar el comportamiento natural

#### Shadowing
- **Proceso**: Seguir a un usuario durante toda su jornada
- **Ventajas**: Visión completa del flujo de trabajo
- **Desventajas**: Intensivo en tiempo, puede ser intrusivo

**Técnicas específicas**:
- **Protocolo de pensamiento en voz alta**: Usuario verbaliza sus pensamientos
- **Análisis de tareas**: Descomposición detallada de actividades
- **Mapeo de flujos**: Documentación visual de procesos

**Guía para observación efectiva**:
```
Preparación:
- Definir objetivos claros
- Preparar plantillas de observación
- Coordinar con usuarios y supervisores

Durante la observación:
- Mantener discreción
- Tomar notas detalladas
- Registrar excepciones y problemas
- Documentar workarounds

Post-observación:
- Analizar patrones
- Identificar ineficiencias
- Validar hallazgos con usuarios
- Documentar oportunidades de mejora
```

### 3. Encuestas y Cuestionarios

**Descripción**: Recopilación sistemática de información de múltiples stakeholders.

**Cuándo usar**:
- Necesidad de input de muchos usuarios
- Validación de hipótesis con amplia audiencia
- Recopilación de datos cuantitativos
- Limitaciones de tiempo para entrevistas individuales

**Tipos de preguntas**:

#### Preguntas Cerradas
- **Opción múltiple**: "¿Cuál es su departamento? a) Ventas b) Marketing c) IT"
- **Escala Likert**: "¿Qué tan satisfecho está? 1-Muy insatisfecho 5-Muy satisfecho"
- **Sí/No**: "¿Usa actualmente algún sistema de CRM?"

#### Preguntas Abiertas
- **Descriptivas**: "Describa su proceso actual de ventas"
- **Opinión**: "¿Qué mejoraría de la herramienta actual?"
- **Experiencia**: "Cuéntenos sobre un problema reciente que tuvo"

**Diseño de encuestas efectivas**:
1. **Comenzar con preguntas fáciles** para establecer compromiso
2. **Agrupar preguntas por tema** para mantener coherencia
3. **Usar lenguaje claro y simple**
4. **Evitar preguntas tendenciosas**
5. **Incluir opciones "No sé" y "No aplica"**
6. **Limitar la longitud** (máximo 10-15 minutos)

**Herramientas recomendadas**:
- Google Forms (gratuita, fácil de usar)
- SurveyMonkey (funciones avanzadas)
- Typeform (interfaz atractiva)
- Microsoft Forms (integración con Office)

### 4. Talleres de Requerimientos

**Descripción**: Sesiones colaborativas donde múltiples stakeholders trabajan juntos para definir requerimientos.

**Estructura típica de un taller**:

#### Preparación (1-2 semanas antes)
- Identificar participantes clave
- Definir agenda y objetivos
- Preparar materiales y herramientas
- Comunicar expectativas

#### Apertura (30 min)
- Presentaciones
- Objetivos y reglas del taller
- Contexto del proyecto

#### Sesiones de trabajo (2-4 horas)
- Brainstorming de necesidades
- Priorización de requerimientos
- Definición de criterios de aceptación
- Resolución de conflictos

#### Cierre (30 min)
- Resumen de decisiones
- Próximos pasos
- Asignación de responsabilidades

**Técnicas para talleres**:

#### Brainstorming
- **Reglas**: No críticas, cantidad sobre calidad, ideas locas bienvenidas
- **Facilitación**: Timeboxing, participación equitativa
- **Herramientas**: Post-its, pizarras, herramientas digitales

#### Dot Voting
- **Proceso**: Cada participante vota por sus prioridades con stickers
- **Ventajas**: Rápido, visual, democrático
- **Uso**: Priorización de funcionalidades

#### Mapping de procesos
- **Objetivo**: Visualizar flujos de trabajo actuales y futuros
- **Herramientas**: Diagramas de flujo, mapas de proceso
- **Beneficios**: Identificación de gaps y oportunidades

**Roles en el taller**:
- **Facilitador**: Guía la sesión, mantiene el foco
- **Analista**: Documenta y clarifica requerimientos
- **Expertos del dominio**: Aportan conocimiento específico
- **Stakeholders**: Representan diferentes perspectivas

### 5. Casos de Uso

**Descripción**: Descripción narrativa de cómo los usuarios interactúan con el sistema.

**Estructura de un caso de uso**:
```
Nombre: Procesar Orden de Compra
Actor principal: Vendedor
Objetivo: Registrar una nueva orden en el sistema
Precondiciones: Usuario autenticado, cliente registrado
Garantías de éxito: Orden registrada, inventario actualizado

Escenario principal:
1. Vendedor selecciona "Nueva Orden"
2. Sistema muestra formulario de orden
3. Vendedor ingresa datos del cliente
4. Sistema valida que el cliente existe
5. Vendedor agrega productos a la orden
6. Sistema calcula totales automáticamente
7. Vendedor confirma la orden
8. Sistema genera número de orden y notifica

Extensiones:
4a. Cliente no existe:
    4a1. Sistema ofrece crear nuevo cliente
    4a2. Vendedor ingresa datos del cliente
    4a3. Sistema registra cliente
    4a4. Continúa en paso 5

6a. Producto sin stock:
    6a1. Sistema muestra mensaje de advertencia
    6a2. Vendedor puede continuar o cambiar producto
```

**Beneficios de los casos de uso**:
- Enfoque centrado en el usuario
- Fácil comprensión para stakeholders no técnicos
- Base para diseño de pruebas
- Identificación de flujos alternativos

### 6. Historias de Usuario

**Descripción**: Descripciones cortas de funcionalidades desde la perspectiva del usuario.

**Formato estándar**:
```
Como [tipo de usuario]
Quiero [funcionalidad]
Para [beneficio/objetivo]
```

**Ejemplos**:
```
Como gerente de ventas
Quiero ver un dashboard con métricas de mi equipo
Para poder identificar oportunidades de mejora

Como cliente
Quiero poder cancelar mi pedido en línea
Para tener flexibilidad en mis compras

Como administrador del sistema
Quiero poder generar reportes de uso
Para optimizar el rendimiento del sistema
```

**Criterios INVEST para historias de usuario**:
- **Independent**: Independientes entre sí
- **Negotiable**: Abiertas a discusión
- **Valuable**: Aportan valor al usuario
- **Estimable**: Se puede estimar el esfuerzo
- **Small**: Pequeñas, implementables en una iteración
- **Testable**: Se pueden probar objetivamente

**Técnica de Story Mapping**:
1. **Identificar actividades principales** del usuario
2. **Desglosar en tareas específicas**
3. **Priorizar por valor e importancia**
4. **Organizar en releases** incrementales

### 7. Prototipos

**Descripción**: Representaciones tempranas del sistema para validar conceptos y requerimientos.

**Tipos de prototipos**:

#### Prototipos de Baja Fidelidad
- **Características**: Sketches, wireframes, mockups simples
- **Ventajas**: Rápidos, baratos, fáciles de cambiar
- **Herramientas**: Papel y lápiz, Balsamiq, Figma
- **Uso**: Exploración inicial de conceptos

#### Prototipos de Alta Fidelidad
- **Características**: Diseño detallado, interacciones reales
- **Ventajas**: Representación realista, mejor feedback
- **Herramientas**: Figma, Adobe XD, InVision
- **Uso**: Validación de diseño final

#### Prototipos Funcionales
- **Características**: Código real, funcionalidad limitada
- **Ventajas**: Validación técnica, performance real
- **Herramientas**: Frameworks de desarrollo
- **Uso**: Pruebas de concepto técnico

**Proceso de prototipado**:
1. **Definir objetivos** del prototipo
2. **Seleccionar fidelidad** apropiada
3. **Crear prototipo** iterativamente
4. **Probar con usuarios** reales
5. **Iterar basado** en feedback
6. **Documentar aprendizajes**

### 8. Análisis de Documentos

**Descripción**: Revisión de documentación existente para extraer requerimientos.

**Tipos de documentos a analizar**:
- **Procedimientos operativos**: Manuales, políticas, regulaciones
- **Documentación técnica**: Especificaciones, diagramas, código
- **Documentos de negocio**: Planes estratégicos, reportes
- **Sistemas existentes**: Interfaces, bases de datos, logs

**Proceso de análisis**:
1. **Inventario de documentos** disponibles
2. **Clasificación por relevancia** y calidad
3. **Extracción de información** pertinente
4. **Identificación de gaps** e inconsistencias
5. **Validación con stakeholders**

### 9. Focus Groups

**Descripción**: Discusiones dirigidas con grupos pequeños de usuarios representativos.

**Cuándo usar**:
- Exploración de conceptos nuevos
- Validación de ideas con usuarios
- Entendimiento de percepciones y actitudes
- Generación de ideas creativas

**Estructura de un focus group**:
```
Duración: 1.5-2 horas
Participantes: 6-8 personas
Facilitador: 1 persona experimentada
Observadores: 1-2 personas

Agenda:
1. Introducción (15 min)
2. Warm-up (15 min)
3. Temas principales (60 min)
4. Wrap-up (15 min)
5. Conclusiones (15 min)
```

**Mejores prácticas**:
- Seleccionar participantes representativos
- Crear ambiente cómodo y no amenazante
- Usar técnicas de facilitación para evitar dominio de participantes
- Grabar sesiones (con permiso)
- Combinar con otras técnicas para validación

## Técnicas Complementarias

### JAD (Joint Application Development)

**Descripción**: Metodología estructurada que involucra usuarios y desarrolladores en sesiones intensivas.

**Características**:
- Sesiones intensivas de 2-5 días
- Participación de todos los stakeholders clave
- Facilitador neutral experimentado
- Enfoque en consenso y decisiones rápidas

**Fases de JAD**:
1. **Planeación**: Selección de participantes, agenda
2. **Investigación**: Recopilación de información previa
3. **Preparación**: Materiales, logística
4. **Sesión JAD**: Talleres intensivos
5. **Documento final**: Especificación de requerimientos

### Design Thinking

**Descripción**: Enfoque centrado en el usuario que combina empatía, definición, ideación, prototipado y testing.

**Fases**:
1. **Empatizar**: Entender profundamente a los usuarios
2. **Definir**: Sintetizar observaciones en problemas centrales
3. **Idear**: Generar amplio rango de soluciones
4. **Prototipar**: Crear representaciones de ideas
5. **Probar**: Validar con usuarios reales

### Análisis de Stakeholders

**Descripción**: Identificación y análisis de todas las personas que afectan o son afectadas por el proyecto.

**Matriz de stakeholders**:
```
           Alto Interés    Bajo Interés
Alta       Gestionar      Mantener
Influencia atentamente    satisfecho

Baja       Mantener       Monitorear
Influencia informado      (mínimo esfuerzo)
```

**Información a recopilar**:
- Rol y responsabilidades
- Objetivos e intereses
- Influencia y poder
- Actitud hacia el proyecto
- Canales de comunicación preferidos

## Selección de Metodología

### Matriz de Decisión

| Criterio | Entrevistas | Observación | Encuestas | Talleres | Prototipos |
|----------|-------------|-------------|-----------|----------|------------|
| Tiempo disponible | Medio | Alto | Bajo | Alto | Medio |
| Número de usuarios | Bajo | Muy bajo | Alto | Medio | Medio |
| Complejidad del dominio | Alto | Alto | Bajo | Alto | Medio |
| Nivel de detalle requerido | Alto | Alto | Medio | Alto | Alto |
| Presupuesto | Medio | Alto | Bajo | Alto | Alto |

### Factores de Contexto

#### Proyecto Nuevo vs Existente
- **Nuevo**: Énfasis en exploración, entrevistas, talleres
- **Existente**: Observación, análisis de documentos, encuestas

#### Criticidad del Sistema
- **Crítico**: Múltiples técnicas, validación exhaustiva
- **No crítico**: Técnicas ágiles, iteración rápida

#### Cultura Organizacional
- **Jerárquica**: Entrevistas formales, documentación detallada
- **Colaborativa**: Talleres, design thinking, prototipos

#### Dispersión Geográfica
- **Local**: Observación, talleres presenciales
- **Distribuida**: Encuestas, entrevistas virtuales, herramientas colaborativas

## Herramientas y Tecnología

### Herramientas de Documentación
- **Confluence**: Wiki colaborativo
- **Notion**: Documentación estructurada
- **GitBook**: Documentación técnica
- **Microsoft Word/Google Docs**: Documentación tradicional

### Herramientas de Colaboración
- **Miro/Mural**: Pizarras digitales colaborativas
- **Figma**: Diseño y prototipado colaborativo
- **Slack/Teams**: Comunicación del equipo
- **Zoom/Meet**: Reuniones virtuales

### Herramientas de Gestión
- **Jira**: Gestión de requerimientos y seguimiento
- **Trello**: Gestión visual simple
- **Azure DevOps**: Suite completa de desarrollo
- **Requirements tools**: IBM DOORS, Polarion

### Herramientas de Análisis
- **Lucidchart**: Diagramas y mapas de proceso
- **Draw.io**: Diagramación gratuita
- **Visio**: Diagramación empresarial
- **PlantUML**: Diagramas como código

## Mejores Prácticas Generales

### Preparación
1. **Definir objetivos claros** para cada sesión
2. **Investigar el contexto** antes de las sesiones
3. **Preparar materiales** y herramientas necesarias
4. **Establecer expectativas** con participantes

### Durante la Elicitación
1. **Escuchar activamente** y hacer preguntas abiertas
2. **Documentar en tiempo real** o inmediatamente después
3. **Validar entendimiento** parafraseando
4. **Mantener neutralidad** y evitar influir en respuestas

### Post-Elicitación
1. **Analizar y sintetizar** información recopilada
2. **Identificar patrones** y temas recurrentes
3. **Validar hallazgos** con stakeholders
4. **Documentar de manera clara** y estructurada

### Gestión de Expectativas
1. **Comunicar limitaciones** de tiempo y alcance
2. **Explicar el proceso** a los participantes
3. **Dar seguimiento** regular sobre progreso
4. **Gestionar cambios** de manera transparente

## Errores Comunes y Cómo Evitarlos

### Error: Depender de una sola técnica
**Solución**: Combinar múltiples técnicas para validación cruzada

### Error: No involucrar a usuarios finales
**Solución**: Incluir usuarios reales en el proceso, no solo intermediarios

### Error: Documentación excesiva o insuficiente
**Solución**: Adaptar nivel de documentación al contexto del proyecto

### Error: No validar requerimientos
**Solución**: Revisiones regulares con stakeholders, prototipos tempranos

### Error: Ignorar restricciones técnicas
**Solución**: Involucrar al equipo técnico desde el inicio

## Reflexiones Personales

### Lecciones Aprendidas

1. **La elicitación es más arte que ciencia**: Requiere intuición, empatía y habilidades interpersonales
2. **No existe una metodología perfecta**: La clave está en combinar técnicas apropiadamente
3. **Los requerimientos son hipótesis**: Deben validarse constantemente
4. **La comunicación es el factor más crítico**: Más proyectos fallan por comunicación que por técnica

### Consejos Prácticos

#### Para Entrevistas
- Preparar pero ser flexible
- Hacer preguntas de seguimiento
- Prestar atención al lenguaje no verbal
- Grabar si es posible (con permiso)

#### Para Talleres
- Establecer reglas claras desde el inicio
- Gestionar participantes dominantes
- Usar técnicas de facilitación visual
- Documentar decisiones en tiempo real

#### Para Validación
- Usar múltiples perspectivas
- Prototipar temprano y frecuentemente
- No asumir que los usuarios saben lo que quieren
- Validar con usuarios reales, no proxies

### Evolución de la Disciplina

La elicitación de requerimientos está evolucionando hacia:
- **Metodologías más ágiles** e iterativas
- **Mayor énfasis en UX** y design thinking
- **Herramientas digitales** más sofisticadas
- **Integración con DevOps** y entrega continua
- **Uso de AI** para análisis de requerimientos

## Conclusión

La elicitación efectiva de requerimientos es una competencia fundamental que combina metodología estructurada con habilidades interpersonales. No existe una receta única; el éxito radica en seleccionar y adaptar las técnicas apropiadas para cada contexto.

Como profesionales del software, debemos ser facilitadores, traductores y detectives, capaces de descubrir necesidades ocultas, resolver conflictos y construir consenso. La inversión en mejores prácticas de elicitación se traduce directamente en proyectos más exitosos y software que realmente resuelve problemas reales.

La clave está en recordar que detrás de cada requerimiento hay personas con necesidades reales, y nuestro trabajo es entender esas necesidades profundamente para crear soluciones que generen valor genuino.

---

*Documento creado como parte de la documentación personal de mejores prácticas en ingeniería de requerimientos.*
