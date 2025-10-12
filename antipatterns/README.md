# Antipatterns - Qué NO Hacer

> Documentación de errores comunes, malas prácticas y soluciones que NO funcionaron

## 🚫 Por Qué Documentar Antipatterns

- **Evitar repetir errores**
- **Enseñar a la IA qué evitar**
- **Justificar decisiones actuales**
- **Acelerar onboarding de nuevos desarrolladores**

## 📋 Template para Antipatterns

```markdown
# [Nombre del Antipattern]

**Categoría**: [Performance/Security/Maintainability/etc.]
**Severidad**: [Alta/Media/Baja]

## ❌ Qué NO hacer
[Descripción del antipattern]

## 🔍 Por qué es problemático
- Problema 1: [descripción]
- Problema 2: [descripción]

## 💡 Qué hacer en su lugar
[Alternativa recomendada]

## 📊 Experiencia Personal
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

## 🗂️ Categorías Comunes

### Performance Antipatterns
- Queries N+1
- Carga síncrona innecesaria
- Memory leaks
- Bundle size excesivo

### Security Antipatterns  
- Secretos en código
- SQL injection vulnerabilities
- XSS vulnerabilities
- Autenticación débil

### Code Quality Antipatterns
- God objects/functions
- Copy-paste programming
- Premature optimization
- Magic numbers/strings

### Architecture Antipatterns
- Tight coupling
- Circular dependencies  
- Inconsistent data flow
- Missing error handling

## 🎯 Cómo Usar Esta Sección

### Para Desarrolladores
1. **Antes de implementar**: Revisa si tu enfoque está aquí
2. **Durante code review**: Usa como checklist
3. **Al debuggear**: Busca patrones conocidos

### Para IA
```
Antes de sugerir código, revisa mis antipatterns documentados.
Si mi solicitud podría llevar a un antipattern conocido, 
adviérteme y sugiere la alternativa documentada.
```

### Para Nuevos Miembros del Equipo
- Lee esta sección para entender "la manera incorrecta"
- Pregunta si no entiendes por qué algo es problemático
- Sugiere nuevos antipatterns que encuentres

---

*Los antipatterns son experiencias de aprendizaje valiosas*