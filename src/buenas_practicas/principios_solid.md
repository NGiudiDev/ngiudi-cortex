# Principios SOLID

## ¿Qué es SOLID?

SOLID es un acrónimo de 5 principios fundamentales de la programación orientada a objetos, creados por Robert C. Martin (Uncle Bob). Estos principios nos guían hacia un diseño de software más limpio y sostenible.

### Los 5 Principios

- **S** - Single Responsibility Principle (Principio de Responsabilidad Única)
- **O** - Open/Closed Principle (Principio Abierto/Cerrado)
- **L** - Liskov Substitution Principle (Principio de Sustitución de Liskov)
- **I** - Interface Segregation Principle (Principio de Segregación de Interfaces)
- **D** - Dependency Inversion Principle (Principio de Inversión de Dependencias)

## ¿Por qué SOLID?

Los principios SOLID nos ayudan a crear código que es:

- ✅ **Mantenible**: Fácil de modificar y entender
- ✅ **Extensible**: Fácil de agregar nuevas funcionalidades
- ✅ **Testeable**: Fácil de probar unitariamente
- ✅ **Reutilizable**: Componentes que se pueden usar en otros contextos
- ✅ **Escalable**: Puede crecer sin volverse inmanejable

---

## 1. Single Responsibility Principle (SRP)

### Definición
> "Una clase debe tener una sola razón para cambiar"

### Explicación
Cada clase debe tener una única responsabilidad y esa responsabilidad debe estar completamente encapsulada en la clase. Una clase debe hacer una cosa y hacerla bien.

### ❌ Ejemplo Incorrecto
```javascript
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }
  
  // Responsabilidad 1: Gestión de datos del usuario
  getName() { return this.name; }
  getEmail() { return this.email; }
  
  // Responsabilidad 2: Validación (¡VIOLA SRP!)
  validateEmail() {
    return this.email.includes('@');
  }
  
  // Responsabilidad 3: Persistencia (¡VIOLA SRP!)
  save() {
    // lógica para guardar en base de datos
  }
  
  // Responsabilidad 4: Notificaciones (¡VIOLA SRP!)
  sendWelcomeEmail() {
    // lógica para enviar email
  }
}
```

### ✅ Ejemplo Correcto
```javascript
// Una responsabilidad: Gestión de datos del usuario
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }
  
  getName() { return this.name; }
  getEmail() { return this.email; }
}

// Una responsabilidad: Validación
class UserValidator {
  validateEmail(email) {
    return email.includes('@');
  }
}

// Una responsabilidad: Persistencia
class UserRepository {
  save(user) {
    // lógica para guardar en base de datos
  }
}

// Una responsabilidad: Notificaciones
class EmailService {
  sendWelcomeEmail(user) {
    // lógica para enviar email
  }
}
```

### Beneficios
- Código más enfocado y comprensible
- Facilita las pruebas unitarias
- Reduce el acoplamiento
- Cambios en una funcionalidad no afectan otras

---

## 2. Open/Closed Principle (OCP)

### Definición
> "Las entidades de software deben estar abiertas para extensión pero cerradas para modificación"

### Explicación
Debes poder agregar nueva funcionalidad sin modificar el código existente. Esto se logra principalmente a través de abstracciones, herencia y polimorfismo.

### ❌ Ejemplo Incorrecto
```javascript
class Calculator {
  calculate(operation, a, b) {
    if (operation === 'add') {
      return a + b;
    } else if (operation === 'subtract') {
      return a - b;
    } else if (operation === 'multiply') {  // ¡Modificando código existente!
      return a * b;
    }
    // Para agregar división, tendríamos que modificar esta función
  }
}
```

### ✅ Ejemplo Correcto
```javascript
// Abstracción base
class Operation {
  execute(a, b) {
    throw new Error('Método debe ser implementado');
  }
}

// Extensiones concretas
class AddOperation extends Operation {
  execute(a, b) {
    return a + b;
  }
}

class SubtractOperation extends Operation {
  execute(a, b) {
    return a - b;
  }
}

// Nueva funcionalidad SIN modificar código existente
class MultiplyOperation extends Operation {
  execute(a, b) {
    return a * b;
  }
}

class Calculator {
  calculate(operation, a, b) {
    return operation.execute(a, b);
  }
}

// Uso
const calculator = new Calculator();
const result = calculator.calculate(new AddOperation(), 5, 3);
```

### Beneficios
- Menos bugs al agregar features
- Código más estable
- Facilita el mantenimiento
- Promueve la reutilización

---

## 3. Liskov Substitution Principle (LSP)

### Definición
> "Los objetos de las subclases deben poder reemplazar a los objetos de la superclase sin alterar el correcto funcionamiento del programa"

### Explicación
Las clases derivadas deben ser sustituibles por sus clases base sin cambiar la funcionalidad del programa. Las subclases deben fortalecer, no debilitar, el contrato de la clase base.

### ❌ Ejemplo Incorrecto
```javascript
class Bird {
  fly() {
    return "Flying";
  }
}

class Penguin extends Bird {
  fly() {
    throw new Error("Penguins can't fly"); // ¡VIOLA LSP!
  }
}

function makeBirdFly(bird) {
  return bird.fly(); // Falla si recibe un Penguin
}
```

### ✅ Ejemplo Correcto
```javascript
class Bird {
  move() {
    return "Moving";
  }
}

class FlyingBird extends Bird {
  fly() {
    return "Flying";
  }
  
  move() {
    return this.fly();
  }
}

class SwimmingBird extends Bird {
  swim() {
    return "Swimming";
  }
  
  move() {
    return this.swim();
  }
}

class Eagle extends FlyingBird {}
class Penguin extends SwimmingBird {}

function makeBirdMove(bird) {
  return bird.move(); // Funciona con cualquier tipo de bird
}
```

### Beneficios
- Herencia correcta y predecible
- Polimorfismo confiable
- Código más robusto
- Facilita las pruebas

---

## 4. Interface Segregation Principle (ISP)

### Definición
> "Los clientes no deben verse obligados a depender de interfaces que no utilizan"

### Explicación
Es mejor tener muchas interfaces específicas que una interfaz general. Las clases no deben ser forzadas a implementar métodos que no necesitan.

### ❌ Ejemplo Incorrecto
```javascript
// Interfaz muy grande y general
class Machine {
  print() { throw new Error('Not implemented'); }
  scan() { throw new Error('Not implemented'); }
  fax() { throw new Error('Not implemented'); }
}

class SimplePrinter extends Machine {
  print() {
    return "Printing...";
  }
  
  scan() {
    throw new Error("Not supported"); // ¡Implementación vacía!
  }
  
  fax() {
    throw new Error("Not supported"); // ¡Implementación vacía!
  }
}
```

### ✅ Ejemplo Correcto
```javascript
// Interfaces específicas y cohesivas
class Printer {
  print() { throw new Error('Not implemented'); }
}

class Scanner {
  scan() { throw new Error('Not implemented'); }
}

class FaxMachine {
  fax() { throw new Error('Not implemented'); }
}

// Implementaciones específicas
class SimplePrinter extends Printer {
  print() {
    return "Printing...";
  }
}

class MultiFunctionDevice extends Printer {
  constructor() {
    super();
    this.scanner = new ScannerImpl();
    this.faxMachine = new FaxImpl();
  }
  
  print() {
    return "Printing...";
  }
  
  scan() {
    return this.scanner.scan();
  }
  
  fax() {
    return this.faxMachine.fax();
  }
}
```

### Beneficios
- Interfaces más cohesivas y específicas
- Menos dependencias innecesarias
- Mayor flexibilidad en implementaciones
- Código más limpio y enfocado

---

## 5. Dependency Inversion Principle (DIP)

### Definición
> "Los módulos de alto nivel no deben depender de módulos de bajo nivel. Ambos deben depender de abstracciones"

### Explicación
Las clases deben depender de abstracciones (interfaces) en lugar de implementaciones concretas. Esto se logra comúnmente mediante inyección de dependencias.

### ❌ Ejemplo Incorrecto
```javascript
class EmailService {
  send(message) {
    // lógica específica de email
    return `Email sent: ${message}`;
  }
}

class NotificationService {
  constructor() {
    this.emailService = new EmailService(); // ¡Dependencia directa!
  }
  
  sendNotification(message) {
    return this.emailService.send(message);
  }
}
```

### ✅ Ejemplo Correcto
```javascript
// Abstracción
class MessageService {
  send(message) {
    throw new Error('Method must be implemented');
  }
}

// Implementaciones concretas
class EmailService extends MessageService {
  send(message) {
    return `Email sent: ${message}`;
  }
}

class SMSService extends MessageService {
  send(message) {
    return `SMS sent: ${message}`;
  }
}

class SlackService extends MessageService {
  send(message) {
    return `Slack message sent: ${message}`;
  }
}

// Clase de alto nivel que depende de la abstracción
class NotificationService {
  constructor(messageService) {
    this.messageService = messageService; // Inyección de dependencia
  }
  
  sendNotification(message) {
    return this.messageService.send(message);
  }
}

// Uso con diferentes implementaciones
const emailNotifier = new NotificationService(new EmailService());
const smsNotifier = new NotificationService(new SMSService());
const slackNotifier = new NotificationService(new SlackService());
```

### Beneficios
- Código más flexible y testeable
- Facilita el cambio de implementaciones
- Reduce el acoplamiento
- Mejora la modularidad

---

## Cuándo Aplicar SOLID

### ✅ Aplicar cuando:
- Proyecto mediano/grande
- Equipo de múltiples desarrolladores
- Código que cambiará frecuentemente
- Sistema que debe ser extensible
- Necesitas alta testabilidad

### ⚠️ Considerar simplicidad cuando:
- Proyecto muy pequeño (menos de 1000 líneas)
- Prototipo rápido
- Código que no cambiará
- Scripts de una sola ejecución
- Deadline muy ajustado

---

## Checklist SOLID

### ✅ SRP (Single Responsibility Principle)
- [ ] ¿La clase tiene una sola razón para cambiar?
- [ ] ¿Puedo describir la clase en una frase sin usar "y"?
- [ ] ¿Los métodos están relacionados con la responsabilidad principal?

### ✅ OCP (Open/Closed Principle)
- [ ] ¿Puedo agregar funcionalidad sin modificar código existente?
- [ ] ¿Uso abstracciones para extensibilidad?
- [ ] ¿Las nuevas features se implementan como extensiones?

### ✅ LSP (Liskov Substitution Principle)
- [ ] ¿Las subclases pueden reemplazar a la clase base completamente?
- [ ] ¿No rompo el contrato en las implementaciones?
- [ ] ¿Las precondiciones no son más fuertes en las subclases?
- [ ] ¿Las postcondiciones no son más débiles en las subclases?

### ✅ ISP (Interface Segregation Principle)
- [ ] ¿Las interfaces son específicas y cohesivas?
- [ ] ¿Los clientes solo dependen de lo que realmente usan?
- [ ] ¿Evito interfaces "gordas" con muchos métodos?

### ✅ DIP (Dependency Inversion Principle)
- [ ] ¿Dependo de abstracciones, no de concreciones?
- [ ] ¿Uso inyección de dependencias?
- [ ] ¿Las clases de alto nivel no conocen detalles de implementación?

---

## Resumen de Beneficios

| Principio | Qué dice | Beneficio principal | Detectar violación |
|-----------|----------|-------------------|-------------------|
| **SRP** | Una clase, una responsabilidad | Código más enfocado | Clase difícil de describir |
| **OCP** | Abierto para extensión, cerrado para modificación | Menos bugs al agregar features | Modificar código para nueva funcionalidad |
| **LSP** | Los subtipos deben ser sustituibles | Herencia correcta | Subclases que rompen comportamiento |
| **ISP** | Interfaces específicas, no generales | Menos dependencias | Implementaciones vacías |
| **DIP** | Depender de abstracciones | Código más flexible | Dependencias directas a clases concretas |
