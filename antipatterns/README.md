# 🔴 Antipatrones - Qué NO Hacer

> Documentación de errores comunes, malas prácticas y soluciones que probablemente no funcionaron

## � Guía de Documentación de Antipatrones

### 🎯 Propósito
Los antipatrones documentan **errores que realmente cometí** y soluciones que parecían buenas ideas pero resultaron problemáticas. Cada antipatrón incluye:
- ❌ **Qué NO hacer** (descripción clara del problema)
- 🔍 **Por qué es problemático** (consecuencias reales)
- ✅ **Qué hacer en su lugar** (alternativa comprobada)
- 💭 **Experiencia personal** (cuándo me pasó, qué aprendí)

### 📝 Cuándo Documentar un Antipatrón

✅ **SÍ documentar**:
- Errores que cometí y causaron problemas reales
- Prácticas que parecían buenas pero no escalaron
- Soluciones que funcionaban a corto plazo pero fallaron después
- Patrones que vi fallar en múltiples proyectos
- Decisiones que tuve que revertir después

❌ **NO documentar**:
- Errores triviales o de sintaxis
- Problemas específicos de un proyecto único
- Teorías sin experiencia práctica
- Antipatrones obvios o bien conocidos sin contexto personal

### 📋 Template Estándar
```markdown
# [Nombre del Antipatrón]

**🏷️ Categoría**: [Performance/Security/Maintainability/etc.]  
**⚡ Severidad**: [Alta/Media/Baja]

## ❌ Qué NO hacer
[Descripción clara del antipatrón con ejemplo de código]

## 🔍 Por qué es problemático
- Problema 1: [descripción específica]
- Problema 2: [consecuencia observada]
- Problema 3: [impacto a largo plazo]

## ✅ Qué hacer en su lugar
[Alternativa recomendada con ejemplo]

## � Experiencia Personal
- **Cuándo me pasó**: [contexto del proyecto]
- **Qué síntomas observé**: [cómo se manifestó el problema]
- **Cómo lo resolví**: [pasos específicos tomados]
- **Lección aprendida**: [insight clave]

## 📊 Impacto
- ⚠️ **Severidad**: [cuánto daño puede causar]
- 🕐 **Detección**: [qué tan fácil es darse cuenta]
- 🔧 **Solución**: [qué tan difícil es arreglar]
```

## 📚 Índice de Antipatrones

### 🏗️ Arquitectura
*Decisiones de estructura que no escalaron*

### 🔒 Seguridad  
*Prácticas que comprometieron la seguridad*

### 🚀 Performance
*Optimizaciones que empeoraron el rendimiento*

### 🧪 Testing
*Estrategias de testing que fallaron*

### 📦 Dependencias
*Gestión de librerías que causó problemas*
- **Cuándo lo encontré**: [contexto]
- **Consecuencias**: [qué pasó]
- **Cómo lo solucioné**: [pasos]

## 🚨 Señales de Alerta
- [Indicador 1]
- [Indicador 2]

## 📝 Ejemplo
```[lenguaje]
// ❌ Antipattern
código problemático

// ✅ Solución recomendada  
código mejorado
```
```

## 🎯 Principios para Documentar Antipatrones

### 💭 Experiencia Real
- **Solo documenta errores que realmente cometiste**
- Incluye el contexto específico donde pasó
- Explica las consecuencias observadas, no teóricas

### 🔍 Enfoque en Síntomas
- **Describe las señales de alerta** que viste
- Explica cómo se manifestó el problema
- Incluye métricas o evidencia cuando sea posible

### ✅ Soluciones Probadas
- **Recomienda solo alternativas que funcionaron**
- Incluye ejemplos de código real
- Explica por qué la nueva solución es mejor

### 🎯 Orientado a Prevención
- **Ayuda a detectar el problema temprano**
- Explica cuándo es más probable que ocurra
- Proporciona herramientas para evitarlo

## 🚨 Niveles de Severidad

### ⚡ Alta
- **Problemas que afectan producción**
- Vulnerabilidades de seguridad
- Performance crítico
- Pérdida de datos

### ⚡ Media  
- **Problemas de mantenibilidad**
- Deuda técnica significativa
- Performance no crítico
- UX degradada

### ⚡ Baja
- **Problemas cosméticos**
- Convenciones no seguidas
- Optimizaciones menores
- Code smells

## 🎯 Cómo Usar Esta Sección

### Para Desarrollo Personal
1. **Antes de implementar**: Revisa si tu enfoque está documentado aquí
2. **Durante code review**: Usa como checklist de problemas conocidos
3. **Al debuggear**: Busca patrones similares a problemas pasados

### Para IA Assistant
- **Antes de sugerir código**: Revisa antipatrones documentados
- **Si detectas un patrón problemático**: Advierte y sugiere alternativa
- **Usa experiencias pasadas**: Para validar nuevas propuestas

---

**📅 Última actualización**: 2025-10-12  
**🎯 Próximo**: Documentar antipatrones de gestión de dependencias y performance