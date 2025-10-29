# Principios DRY, KISS y YAGNI

## Introducción

Estos tres principios son pilares fundamentales del desarrollo de software moderno que, cuando se aplican correctamente, resultan en código más limpio, mantenible y eficiente. Aunque son conceptos simples, su aplicación práctica puede tener un impacto significativo en la calidad del software.

---

## 1. DRY - Don't Repeat Yourself

### Definición
> "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system"
> 
> *"Cada pieza de conocimiento debe tener una representación única, no ambigua y autoritativa dentro de un sistema"*

### Explicación
El principio DRY establece que no debes duplicar lógica o conocimiento en tu código. Cuando encuentres código repetido, debes extraerlo a una función, clase o módulo reutilizable.

### Tipos de Duplicación

#### 1. **Duplicación de Código**
```javascript
// ❌ Ejemplo Incorrecto - Código duplicado
function calculateAreaRectangle(width, height) {
  if (width <= 0 || height <= 0) {
    throw new Error('Dimensions must be positive');
  }
  return width * height;
}

function calculateAreaTriangle(base, height) {
  if (base <= 0 || height <= 0) {
    throw new Error('Dimensions must be positive');
  }
  return (base * height) / 2;
}

function calculateAreaCircle(radius) {
  if (radius <= 0) {
    throw new Error('Radius must be positive');
  }
  return Math.PI * radius * radius;
}
```

```javascript
// ✅ Ejemplo Correcto - DRY aplicado
function validatePositive(...values) {
  if (values.some(value => value <= 0)) {
    throw new Error('All values must be positive');
  }
}

function calculateAreaRectangle(width, height) {
  validatePositive(width, height);
  return width * height;
}

function calculateAreaTriangle(base, height) {
  validatePositive(base, height);
  return (base * height) / 2;
}

function calculateAreaCircle(radius) {
  validatePositive(radius);
  return Math.PI * radius * radius;
}
```

#### 2. **Duplicación de Configuración**
```javascript
// ❌ Ejemplo Incorrecto - Configuración duplicada
const devConfig = {
  database: {
    host: 'localhost',
    port: 5432,
    ssl: false,
    timeout: 30000
  },
  api: {
    timeout: 30000,
    retries: 3
  }
};

const prodConfig = {
  database: {
    host: 'prod-server',
    port: 5432,
    ssl: true,
    timeout: 30000
  },
  api: {
    timeout: 30000,
    retries: 3
  }
};
```

```javascript
// ✅ Ejemplo Correcto - DRY en configuración
const baseConfig = {
  database: {
    port: 5432,
    timeout: 30000
  },
  api: {
    timeout: 30000,
    retries: 3
  }
};

const devConfig = {
  ...baseConfig,
  database: {
    ...baseConfig.database,
    host: 'localhost',
    ssl: false
  }
};

const prodConfig = {
  ...baseConfig,
  database: {
    ...baseConfig.database,
    host: 'prod-server',
    ssl: true
  }
};
```

### Técnicas para Aplicar DRY

#### 1. **Extracción de Funciones**
```javascript
// ❌ Antes
function processUsers(users) {
  return users
    .filter(user => user.active)
    .map(user => ({
      ...user,
      name: user.name.trim().toLowerCase()
    }));
}

function processProducts(products) {
  return products
    .filter(product => product.active)
    .map(product => ({
      ...product,
      name: product.name.trim().toLowerCase()
    }));
}

// ✅ Después
function normalizeString(str) {
  return str.trim().toLowerCase();
}

function filterActive(items) {
  return items.filter(item => item.active);
}

function normalizeNames(items) {
  return items.map(item => ({
    ...item,
    name: normalizeString(item.name)
  }));
}

function processUsers(users) {
  return normalizeNames(filterActive(users));
}

function processProducts(products) {
  return normalizeNames(filterActive(products));
}
```

#### 2. **Uso de Parámetros y Configuración**
```javascript
// ❌ Antes - Múltiples funciones similares
function sendEmailNotification(user, message) {
  return fetch('/api/notifications/email', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ user, message, type: 'email' })
  });
}

function sendSMSNotification(user, message) {
  return fetch('/api/notifications/sms', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ user, message, type: 'sms' })
  });
}

// ✅ Después - Función parametrizada
function sendNotification(user, message, type) {
  return fetch(`/api/notifications/${type}`, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ user, message, type })
  });
}

// Funciones wrapper específicas si es necesario
const sendEmail = (user, message) => sendNotification(user, message, 'email');
const sendSMS = (user, message) => sendNotification(user, message, 'sms');
```

### Cuándo NO Aplicar DRY

#### 1. **Duplicación Accidental**
```javascript
// ✅ Está bien duplicar si el contexto es diferente
function validateUserEmail(email) {
  return email && email.includes('@'); // Validación simple para usuarios
}

function validateAdminEmail(email) {
  return email && email.includes('@'); // Podría volverse más compleja
}
```

#### 2. **Abstracción Prematura**
```javascript
// ⚠️ Cuidado - No forzar DRY si no hay certeza del patrón
function calculateTax(amount) {
  return amount * 0.21; // España
}

function calculateDiscount(amount) {
  return amount * 0.21; // Descuento del 21%
}

// Aunque ambos usan 0.21, representan conceptos diferentes
// La abstracción sería prematura aquí
```

### Beneficios del DRY
- **Mantenibilidad**: Cambios en una sola ubicación
- **Consistencia**: Comportamiento uniforme en toda la aplicación
- **Reducción de bugs**: Menos lugares donde pueden ocurrir errores
- **Facilita testing**: Menos código que probar

### Riesgos del DRY Excesivo
- **Acoplamiento innecesario**: Abstracciones forzadas
- **Complejidad**: Funciones con demasiados parámetros
- **Inflexibilidad**: Dificultad para cambios específicos

---

## 2. KISS - Keep It Simple, Stupid

### Definición
> "Simplicity should be a key goal in design, and unnecessary complexity should be avoided"
>
> *"La simplicidad debe ser un objetivo clave en el diseño, y se debe evitar la complejidad innecesaria"*

### Explicación
KISS promueve la simplicidad en el diseño y la implementación. El código simple es más fácil de entender, mantener, debuggear y extender.

### Aplicación Práctica

#### 1. **Funciones Simples y Claras**
```javascript
// ❌ Ejemplo Complejo - Difícil de entender
function processUserData(data) {
  return data.users?.filter(u => u?.status === 'active' && u?.profile?.verified === true)
    .map(u => ({
      id: u.id,
      name: u.profile?.firstName + ' ' + (u.profile?.lastName || ''),
      email: u.contact?.email?.toLowerCase() || '',
      lastLogin: u.activity?.lastLogin ? new Date(u.activity.lastLogin) : null
    }))
    .sort((a, b) => (b.lastLogin || new Date(0)) - (a.lastLogin || new Date(0))) || [];
}

// ✅ Ejemplo Simple - Fácil de entender
function isActiveVerifiedUser(user) {
  return user?.status === 'active' && user?.profile?.verified === true;
}

function formatUserName(profile) {
  const firstName = profile?.firstName || '';
  const lastName = profile?.lastName || '';
  return `${firstName} ${lastName}`.trim();
}

function formatUserEmail(contact) {
  return contact?.email?.toLowerCase() || '';
}

function formatLastLogin(activity) {
  return activity?.lastLogin ? new Date(activity.lastLogin) : null;
}

function transformUser(user) {
  return {
    id: user.id,
    name: formatUserName(user.profile),
    email: formatUserEmail(user.contact),
    lastLogin: formatLastLogin(user.activity)
  };
}

function sortByLastLogin(users) {
  return users.sort((a, b) => 
    (b.lastLogin || new Date(0)) - (a.lastLogin || new Date(0))
  );
}

function processUserData(data) {
  if (!data?.users) return [];
  
  const activeUsers = data.users.filter(isActiveVerifiedUser);
  const transformedUsers = activeUsers.map(transformUser);
  return sortByLastLogin(transformedUsers);
}
```

#### 2. **Evitar Sobre-ingeniería**
```javascript
// ❌ Ejemplo Complejo - Sobre-ingeniería
class AbstractFactoryManagerSingleton {
  private static instance: AbstractFactoryManagerSingleton;
  private factories: Map<string, AbstractFactory>;
  
  private constructor() {
    this.factories = new Map();
  }
  
  public static getInstance(): AbstractFactoryManagerSingleton {
    if (!this.instance) {
      this.instance = new AbstractFactoryManagerSingleton();
    }
    return this.instance;
  }
  
  public registerFactory(type: string, factory: AbstractFactory): void {
    this.factories.set(type, factory);
  }
  
  public createProduct(type: string, config: ProductConfig): Product {
    const factory = this.factories.get(type);
    if (!factory) {
      throw new Error(`Factory not found for type: ${type}`);
    }
    return factory.createProduct(config);
  }
}

// ✅ Ejemplo Simple - Directo y claro
const productCreators = {
  email: (config) => new EmailNotification(config),
  sms: (config) => new SMSNotification(config),
  push: (config) => new PushNotification(config)
};

function createNotification(type, config) {
  const creator = productCreators[type];
  if (!creator) {
    throw new Error(`Unknown notification type: ${type}`);
  }
  return creator(config);
}
```

#### 3. **Nombres Descriptivos y Claros**
```javascript
// ❌ Nombres confusos
function calc(x, y, t) {
  if (t === 1) return x + y;
  if (t === 2) return x - y;
  if (t === 3) return x * y;
  return x / y;
}

// ✅ Nombres claros
function performMathOperation(firstNumber, secondNumber, operation) {
  switch (operation) {
    case 'add': return firstNumber + secondNumber;
    case 'subtract': return firstNumber - secondNumber;
    case 'multiply': return firstNumber * secondNumber;
    case 'divide': return firstNumber / secondNumber;
    default: throw new Error('Invalid operation');
  }
}

// ✅ Aún mejor - funciones específicas
const add = (a, b) => a + b;
const subtract = (a, b) => a - b;
const multiply = (a, b) => a * b;
const divide = (a, b) => a / b;
```

#### 4. **Estructuras de Datos Simples**
```javascript
// ❌ Estructura compleja innecesaria
class UserProfileManager {
  private userMap: Map<string, UserProfile>;
  private indexByEmail: Map<string, string>;
  private indexByPhone: Map<string, string>;
  
  constructor() {
    this.userMap = new Map();
    this.indexByEmail = new Map();
    this.indexByPhone = new Map();
  }
  
  addUser(user: UserProfile) {
    this.userMap.set(user.id, user);
    this.indexByEmail.set(user.email, user.id);
    if (user.phone) {
      this.indexByPhone.set(user.phone, user.id);
    }
  }
  
  findByEmail(email: string): UserProfile | undefined {
    const id = this.indexByEmail.get(email);
    return id ? this.userMap.get(id) : undefined;
  }
}

// ✅ Estructura simple para el caso común
class UserManager {
  constructor() {
    this.users = [];
  }
  
  addUser(user) {
    this.users.push(user);
  }
  
  findByEmail(email) {
    return this.users.find(user => user.email === email);
  }
  
  findByPhone(phone) {
    return this.users.find(user => user.phone === phone);
  }
}
```

### Principios de KISS

1. **Una función, una responsabilidad**
2. **Nombres claros y descriptivos**
3. **Evitar anidamiento profundo**
4. **Preferir composición sobre herencia compleja**
5. **Usar estructuras de datos simples cuando sea posible**
6. **Documentar solo lo necesario**

### Beneficios de KISS
- **Legibilidad**: Código fácil de entender
- **Mantenibilidad**: Cambios más simples y seguros
- **Debugging**: Errores más fáciles de encontrar
- **Performance**: Menos complejidad computacional
- **Onboarding**: Nuevos desarrolladores se adaptan más rápido

---

## 3. YAGNI - You Aren't Gonna Need It

### Definición
> "Don't implement something until you actually need it"
>
> *"No implementes algo hasta que realmente lo necesites"*

### Explicación
YAGNI es un principio de la programación extrema (XP) que establece que no debes agregar funcionalidad hasta que sea necesaria. Evita la sobre-ingeniería y el desarrollo especulativo.

### Ejemplos Prácticos

#### 1. **Evitar Funcionalidades Especulativas**
```javascript
// ❌ Ejemplo que viola YAGNI - Implementando "por si acaso"
class UserManager {
  constructor() {
    this.users = [];
    this.deletedUsers = []; // "Por si necesitamos recuperar usuarios"
    this.userAuditLog = []; // "Por si necesitamos auditoría"
    this.userCache = new Map(); // "Por si necesitamos caché"
    this.userIndexes = {
      byEmail: new Map(),
      byPhone: new Map(),
      byDepartment: new Map(), // "Por si buscamos por departamento"
      byRole: new Map(), // "Por si buscamos por rol"
      byCreationDate: new Map() // "Por si necesitamos ordenar por fecha"
    };
  }
  
  addUser(user) {
    this.users.push(user);
    this.userCache.set(user.id, user);
    this.updateAllIndexes(user);
    this.logAction('ADD_USER', user);
  }
  
  deleteUser(userId) {
    const user = this.findUser(userId);
    if (user) {
      this.users = this.users.filter(u => u.id !== userId);
      this.deletedUsers.push({ ...user, deletedAt: new Date() });
      this.userCache.delete(userId);
      this.removeFromAllIndexes(user);
      this.logAction('DELETE_USER', user);
    }
  }
  
  // Métodos complejos para mantener todos los índices
  updateAllIndexes(user) { /* ... */ }
  removeFromAllIndexes(user) { /* ... */ }
  logAction(action, user) { /* ... */ }
}

// ✅ Ejemplo siguiendo YAGNI - Solo lo necesario
class UserManager {
  constructor() {
    this.users = [];
  }
  
  addUser(user) {
    this.users.push(user);
  }
  
  deleteUser(userId) {
    this.users = this.users.filter(u => u.id !== userId);
  }
  
  findUser(userId) {
    return this.users.find(u => u.id === userId);
  }
}

// Cuando realmente necesites búsqueda por email, ENTONCES agregarlo:
class UserManager {
  // ... métodos anteriores ...
  
  findByEmail(email) {
    return this.users.find(u => u.email === email);
  }
}
```

#### 2. **Configurabilidad Excesiva**
```javascript
// ❌ Violando YAGNI - Demasiada configuración "por si acaso"
class APIClient {
  constructor(config = {}) {
    this.baseURL = config.baseURL || 'https://api.example.com';
    this.timeout = config.timeout || 5000;
    this.retries = config.retries || 3;
    this.retryDelay = config.retryDelay || 1000;
    this.exponentialBackoff = config.exponentialBackoff || false;
    this.maxRetryDelay = config.maxRetryDelay || 30000;
    this.authType = config.authType || 'bearer';
    this.apiVersion = config.apiVersion || 'v1';
    this.compression = config.compression || false;
    this.caching = config.caching || false;
    this.cacheTTL = config.cacheTTL || 300000;
    this.requestIdHeader = config.requestIdHeader || 'X-Request-ID';
    this.userAgent = config.userAgent || 'MyApp/1.0';
    this.rateLimiting = config.rateLimiting || false;
    this.rateLimitRequests = config.rateLimitRequests || 100;
    this.rateLimitWindow = config.rateLimitWindow || 60000;
    // ... más configuraciones que "podrían ser útiles"
  }
}

// ✅ Siguiendo YAGNI - Solo configuración necesaria
class APIClient {
  constructor(baseURL) {
    this.baseURL = baseURL;
    this.timeout = 5000; // valor por defecto razonable
  }
  
  async get(endpoint) {
    const response = await fetch(`${this.baseURL}${endpoint}`, {
      method: 'GET',
      signal: AbortSignal.timeout(this.timeout)
    });
    return response.json();
  }
}

// Agregar configuración SOLO cuando sea necesaria:
// Si necesitas timeout configurable:
class APIClient {
  constructor(baseURL, timeout = 5000) {
    this.baseURL = baseURL;
    this.timeout = timeout;
  }
  // ...
}
```

#### 3. **Abstracciones Prematuras**
```javascript
// ❌ Violando YAGNI - Abstracción prematura
interface DatabaseAdapter {
  connect(): Promise<void>;
  disconnect(): Promise<void>;
  query(sql: string, params?: any[]): Promise<any[]>;
  transaction(queries: DatabaseQuery[]): Promise<void>;
  backup(): Promise<string>;
  restore(backupPath: string): Promise<void>;
}

class MySQLAdapter implements DatabaseAdapter {
  // Implementa todos los métodos aunque solo uses query()
}

class PostgreSQLAdapter implements DatabaseAdapter {
  // Implementa todos los métodos aunque solo uses query()
}

class MongoAdapter implements DatabaseAdapter {
  // Fuerza SQL en MongoDB - no tiene sentido
}

// ✅ Siguiendo YAGNI - Empezar simple
class Database {
  constructor(connectionString) {
    this.connectionString = connectionString;
  }
  
  async query(sql, params) {
    // Implementación directa para tu base de datos actual
    return mysql.query(sql, params);
  }
}

// Crear abstracción SOLO cuando necesites múltiples bases de datos
```

### Cómo Aplicar YAGNI

#### 1. **Pregúntate antes de implementar**
- ¿Esto es necesario AHORA?
- ¿Hay un requerimiento específico para esto?
- ¿Está en el backlog actual?
- ¿El cliente lo pidió explícitamente?

#### 2. **Implementa incrementalmente**
```javascript
// ✅ Versión 1 - Solo lo necesario
function sendEmail(to, subject, body) {
  return emailService.send({ to, subject, body });
}

// ✅ Versión 2 - Cuando necesites CC
function sendEmail(to, subject, body, cc = null) {
  const email = { to, subject, body };
  if (cc) email.cc = cc;
  return emailService.send(email);
}

// ✅ Versión 3 - Cuando necesites attachments
function sendEmail(to, subject, body, options = {}) {
  const email = { to, subject, body };
  if (options.cc) email.cc = options.cc;
  if (options.attachments) email.attachments = options.attachments;
  return emailService.send(email);
}
```

#### 3. **Refactoriza cuando sea necesario**
```javascript
// ✅ Empezar simple
const users = [
  { id: 1, name: 'John', email: 'john@email.com' },
  { id: 2, name: 'Jane', email: 'jane@email.com' }
];

function findUser(id) {
  return users.find(user => user.id === id);
}

// ✅ Refactorizar SOLO cuando el performance se vuelva un problema
const userMap = new Map(users.map(user => [user.id, user]));

function findUser(id) {
  return userMap.get(id);
}
```

### Señales de Violación de YAGNI

- 🚩 "Por si acaso necesitamos..."
- 🚩 "En el futuro podríamos..."
- 🚩 "Esto nos dará flexibilidad para..."
- 🚩 Configuraciones que nunca se usan
- 🚩 Parámetros opcionales que no tienen casos de uso
- 🚩 Abstracciones con una sola implementación
- 🚩 Funcionalidades que han estado "en desarrollo" por meses

### Beneficios de YAGNI
- **Menos código**: Menos bugs y menos mantenimiento
- **Desarrollo más rápido**: Enfoque en lo importante
- **Mejor diseño**: Decisiones basadas en necesidades reales
- **Menos complejidad**: Sistema más simple y comprensible
- **Mejor ROI**: Tiempo invertido en valor real

---

## Combinando los Tres Principios

### Ejemplo Integrado
```javascript
// ✅ Aplicando DRY + KISS + YAGNI
class TodoManager {
  constructor() {
    this.todos = []; // YAGNI: empezar simple, sin base de datos
  }
  
  // KISS: función simple y clara
  addTodo(text) {
    const todo = {
      id: Date.now(), // YAGNI: ID simple, sin UUID por ahora
      text,
      completed: false,
      createdAt: new Date()
    };
    this.todos.push(todo);
    return todo;
  }
  
  // DRY: reutilizar lógica de búsqueda
  findTodo(id) {
    return this.todos.find(todo => todo.id === id);
  }
  
  // KISS: operación directa
  toggleTodo(id) {
    const todo = this.findTodo(id); // DRY: reutilizar findTodo
    if (todo) {
      todo.completed = !todo.completed;
    }
    return todo;
  }
  
  // KISS: filtros simples
  getCompletedTodos() {
    return this.todos.filter(todo => todo.completed);
  }
  
  getPendingTodos() {
    return this.todos.filter(todo => !todo.completed);
  }
}

// Ejemplo de evolución siguiendo los principios:

// Si DESPUÉS necesitas persistencia (YAGNI):
class TodoManager {
  constructor(storage = null) { // YAGNI: agregar solo cuando necesites
    this.todos = [];
    this.storage = storage;
  }
  
  async addTodo(text) {
    const todo = this.createTodo(text); // DRY: extraer creación
    this.todos.push(todo);
    if (this.storage) {
      await this.storage.save(todo); // KISS: delegar a storage
    }
    return todo;
  }
  
  // DRY: extraer lógica de creación cuando sea necesaria
  createTodo(text) {
    return {
      id: Date.now(),
      text,
      completed: false,
      createdAt: new Date()
    };
  }
}
```

---

## Checklist de Aplicación

### ✅ DRY (Don't Repeat Yourself)
- [ ] ¿Hay código duplicado que pueda extraerse?
- [ ] ¿Las constantes están centralizadas?
- [ ] ¿La lógica de validación está reutilizada?
- [ ] ¿Los patrones comunes están abstraídos?
- [ ] ¿Evito la duplicación de conocimiento de negocio?

### ✅ KISS (Keep It Simple, Stupid)
- [ ] ¿Puede un desarrollador nuevo entender este código?
- [ ] ¿Estoy usando la solución más simple que funciona?
- [ ] ¿Los nombres son claros y descriptivos?
- [ ] ¿Evito anidamiento profundo (> 3 niveles)?
- [ ] ¿Las funciones tienen una sola responsabilidad?

### ✅ YAGNI (You Aren't Gonna Need It)
- [ ] ¿Esta funcionalidad es necesaria AHORA?
- [ ] ¿Hay un requerimiento específico para esto?
- [ ] ¿Evito configuraciones "por si acaso"?
- [ ] ¿Me enfoco en el caso de uso actual?
- [ ] ¿Puedo implementar esto incrementalmente cuando sea necesario?

---

## Cuándo Aplicar Cada Principio

### Contextos de Aplicación

| Principio | Cuándo Aplicar | Cuándo Ser Flexible |
|-----------|----------------|-------------------|
| **DRY** | Lógica de negocio repetida | Código similar en contextos diferentes |
| **KISS** | Siempre que sea posible | Cuando la complejidad sea inherente al dominio |
| **YAGNI** | Funcionalidades especulativas | APIs públicas que necesitan estabilidad |

### Señales de Alarma

| Principio | Señal de Violación | Acción Correctiva |
|-----------|-------------------|-------------------|
| **DRY** | Copy-paste frecuente | Extraer función/módulo común |
| **KISS** | Código difícil de explicar | Dividir en funciones más pequeñas |
| **YAGNI** | "Por si acaso..." | Implementar solo cuando sea necesario |

---

## Herramientas y Métricas

### Detección de Violaciones
- **ESLint rules**: `no-duplicate-code`, `complexity`
- **SonarQube**: Detecta duplicación y complejidad
- **Code Climate**: Métricas de mantenibilidad
- **PMD/SpotBugs**: Para Java

### Métricas Útiles
- **Cyclomatic Complexity**: Mide complejidad (KISS)
- **Code Duplication %**: Porcentaje de código duplicado (DRY)
- **Lines of Code**: Indicador de simplicity (YAGNI + KISS)
- **Function Length**: Funciones largas violan KISS

---

## Conclusión

Los principios DRY, KISS y YAGNI forman un conjunto poderoso de guías que, aplicadas consistentemente, resultan en código más mantenible, comprensible y eficiente. La clave está en encontrar el equilibrio correcto y aplicar cada principio en el contexto apropiado.

### Resumen de Beneficios
- **DRY**: Reduce mantenimiento y aumenta consistencia
- **KISS**: Mejora legibilidad y facilita debugging
- **YAGNI**: Acelera desarrollo y reduce complejidad innecesaria

### La Regla de Oro
> "Haz el código tan simple como sea posible, pero no más simple" - Albert Einstein (adaptado)

Recuerda: estos principios son guías, no reglas absolutas. El buen juicio y el contexto específico del proyecto siempre deben considerarse al aplicarlos.