# Modules em Node.js

Este README explora os conceitos fundamentais dos módulos em Node.js, abordando os formatos comuns, a criação de módulos personalizados e o uso da palavra-chave `global`.

## Índice

1. [Common Formats: CommonJS e ESM](#common-formats-commonjs-esm)
2. [Creating Custom Modules](#creating-custom-modules)
3. [`global` Keyword](#global-keyword)

## 1. Common Formats: CommonJS e ESM

### CommonJS (CJS)
O formato CommonJS é o sistema de módulos padrão do Node.js. Ele utiliza a função `require` para importar módulos e a variável `module.exports` para exportá-los.

#### Exemplo: Importando e Exportando com CommonJS

**`math.js`**
```javascript
// math.js
const add = (a, b) => a + b;
const subtract = (a, b) => a - b;

module.exports = { add, subtract };
```

**`app.js`**
```javascript
// app.js
const math = require('./math');

console.log(math.add(5, 3));  // Saída: 8
console.log(math.subtract(5, 3));  // Saída: 2
```

### ES Modules (ESM)
Os ES Modules são a implementação de módulos nativos do JavaScript (ECMAScript) e são suportados a partir do Node.js 12. Eles utilizam as palavras-chave `import` e `export`.

#### Exemplo: Importando e Exportando com ESM

**`math.mjs`**
```javascript
// math.mjs
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
```

**`app.mjs`**
```javascript
// app.mjs
import { add, subtract } from './math.mjs';

console.log(add(5, 3));  // Saída: 8
console.log(subtract(5, 3));  // Saída: 2
```

### Diferenças Principais entre CommonJS e ESM
- **Carregamento**: CommonJS carrega módulos de forma síncrona, enquanto o ESM suporta carregamento assíncrono.
- **Palavras-chave**: CommonJS usa `require` e `module.exports`, enquanto ESM usa `import` e `export`.
- **Escopo**: No CommonJS, o escopo do módulo é local. No ESM, o escopo é estritamente por módulo, promovendo práticas de encapsulamento.

## 2. Creating Custom Modules

Em Node.js, criar módulos personalizados é simples. Qualquer arquivo JavaScript pode ser transformado em um módulo.

### Exemplo: Criando e Utilizando um Módulo Personalizado

**`greeting.js`**
```javascript
// greeting.js
const greet = (name) => `Hello, ${name}!`;

module.exports = greet;
```

**`app.js`**
```javascript
// app.js
const greet = require('./greeting');

console.log(greet('World'));  // Saída: Hello, World!
```

Neste exemplo, `greeting.js` define uma função `greet` e a exporta usando `module.exports`. Em `app.js`, o módulo `greeting` é importado e utilizado.

## 3. `global` Keyword

A palavra-chave `global` em Node.js é usada para declarar variáveis globais que podem ser acessadas em qualquer lugar da aplicação. No entanto, o uso de variáveis globais é geralmente desencorajado, pois pode levar a conflitos e problemas de manutenção.

### Exemplo: Usando `global`

**`app.js`**
```javascript
// app.js
global.greeting = "Hello, World!";

console.log(global.greeting);  // Saída: Hello, World!
```

Neste exemplo, a variável `greeting` é definida no objeto `global`, tornando-a acessível em qualquer arquivo dentro do ambiente Node.js.

## Conclusão

Este README abordou os formatos comuns de módulos em Node.js, incluindo CommonJS e ES Modules, além de como criar módulos personalizados e usar a palavra-chave `global`. Entender esses conceitos é fundamental para estruturar suas aplicações de forma modular e eficiente.
