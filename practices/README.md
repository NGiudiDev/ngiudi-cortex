# Buenas Prácticas de Desarrollo

> Principios y prácticas que sigo consistentemente en todos mis proyectos

## 📝 Documentación de Código

### Comentarios
- **Explica el "por qué", no el "qué"**
- Usa comentarios para contexto de negocio
- Documenta decisiones no obvias
- Evita comentarios que repiten el código

```javascript
// ❌ Malo
let price = price * 1.21; // Multiplica por 1.21

// ✅ Bueno  
let price = price * 1.21; // Aplica IVA (21%) según regulación argentina
```

### Nombres Descriptivos
- Variables y funciones deben explicar su propósito
- Usa nombres que se lean como oraciones en inglés
- Evita abreviaciones ambiguas

## 🏗️ Arquitectura de Código

### Principio de Responsabilidad Única
- Cada función/clase tiene una sola razón para cambiar
- Funciones pequeñas y específicas
- Clases cohesivas

### Separación de Concerns
- Lógica de negocio separada de UI
- Datos separados de presentación
- Configuración separada de implementación

## 🧪 Testing

### Pirámide de Testing
1. **Unit Tests** (70%): Funciones individuales
2. **Integration Tests** (20%): Interacción entre módulos  
3. **E2E Tests** (10%): Flujos completos de usuario

### Principios de Testing
- Tests como documentación viva
- Un concepto por test
- Nombres descriptivos que explican el comportamiento
- Arrange, Act, Assert pattern

## 🔒 Seguridad

### Input Validation
- Validar TODOS los inputs del usuario
- Sanitizar datos antes de procesarlos
- Usar whitelist en lugar de blacklist

### Secretos y Configuración
- NUNCA secretos en código
- Variables de entorno para configuración
- Diferentes configs por ambiente

## 📦 Gestión de Dependencias

### Criterios para Elegir Librerías
1. **Mantenimiento activo**: Commits recientes
2. **Comunidad**: Issues resueltas, documentación
3. **Tamaño**: Bundle size impact
4. **Licencia**: Compatible con el proyecto
5. **Estabilidad**: Versiones y breaking changes

### Versionado
- Semantic Versioning (SemVer)
- Lock files siempre en repo
- Actualizar dependencias regularmente

## 🚀 Performance

### Optimización Prematura
- "Premature optimization is the root of all evil"
- Medir antes de optimizar
- Optimizar cuellos de botella identificados

### Principios Generales
- Lazy loading cuando sea posible
- Cache inteligente
- Minimizar requests HTTP
- Optimizar assets (imágenes, bundles)

## 📁 Organización de Proyectos

### Estructura de Carpetas
TODO: actualizar esta sección
```
src/
  components/     # Componentes reutilizables
  pages/         # Páginas/vistas principales  
  services/      # Lógica de negocio
  utils/         # Funciones utilitarias
  types/         # Definiciones de tipos
  constants/     # Constantes de la app
  config/        # Configuración
  assets/        # Recursos estáticos
```

### Convenciones de Naming
- **Archivos**: kebab-case o camelCase consistente
- **Componentes**: PascalCase
- **Variables/Funciones**: camelCase
- **Constantes**: SCREAMING_SNAKE_CASE

---

*Estas prácticas evolucionan con la experiencia. Fecha última actualización: 2025-01-01*