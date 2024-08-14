# Introdução ao Node.js

Bem-vindo a esta introdução ao Node.js! Este README cobrirá os conceitos fundamentais do Node.js, incluindo sua definição, razões para uso, história, diferenças em relação aos ambientes de navegador e como executar código Node.js. Cada seção é projetada para fornecer uma compreensão clara, juntamente com exemplos para ajudar você a começar.

---

### Tabela de Conteúdos
- [O que é Node.js?](#o-que-é-nodejs)
- [Por que usar Node.js?](#por-que-usar-nodejs)
- [História do Node.js](#história-do-nodejs)
- [Node.js vs Navegador](#nodejs-vs-navegador)
- [Executando Código Node.js](#executando-código-nodejs)

---

### O que é Node.js?

**Node.js** é um ambiente de execução JavaScript construído sobre o motor JavaScript V8 do Chrome. Ele permite que os desenvolvedores executem código JavaScript fora de um navegador, possibilitando a construção de aplicativos e ferramentas do lado do servidor com JavaScript.

O Node.js oferece uma rica biblioteca de módulos que simplificam o desenvolvimento de servidores web, sistemas de arquivos, redes e outros serviços de back-end.

**Exemplo:**

```javascript
// Importando o módulo HTTP nativo
const http = require('http');

// Criando um servidor HTTP simples
const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Olá, Mundo!');
});

// O servidor escuta na porta 3000
server.listen(3000, () => {
  console.log('Servidor rodando em http://localhost:3000/');
});
```

Este exemplo demonstra um servidor HTTP simples que responde com "Olá, Mundo!" a qualquer requisição.

---

### Por que usar Node.js?

O Node.js é popular por várias razões:

1. **Assíncrono e Baseado em Eventos**: O Node.js é projetado para lidar com operações assíncronas, tornando-o eficiente para tarefas dependentes de I/O, como lidar com múltiplas requisições simultâneas.

2. **Linguagem de Programação Única**: Os desenvolvedores podem usar JavaScript tanto no front-end quanto no back-end, facilitando o gerenciamento de código e a consistência.

3. **Grande Ecossistema**: Com o npm (Node Package Manager), o Node.js possui um vasto ecossistema de bibliotecas e ferramentas open-source que aceleram o desenvolvimento.

4. **Escalabilidade**: O Node.js pode lidar com um grande número de conexões simultâneas com alta taxa de transferência, sendo adequado para aplicações em tempo real, como servidores de chat e jogos.

**Exemplo:**

```javascript
// Exemplo de I/O não bloqueante assíncrono
const fs = require('fs');

fs.readFile('exemplo.txt', 'utf8', (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});

console.log('Leitura de arquivo iniciada!');
```

Neste exemplo, a operação de leitura do arquivo é não bloqueante, o que significa que a mensagem "Leitura de arquivo iniciada!" será registrada antes que o conteúdo do arquivo seja impresso.

---

### História do Node.js

O Node.js foi criado por **Ryan Dahl** em 2009. O objetivo era construir aplicativos de rede escaláveis usando JavaScript, que na época era usado principalmente para scripts do lado do cliente. Dahl tinha como objetivo desenvolver uma solução que pudesse lidar com milhares de conexões com tempos de resposta baixos.

Marcos importantes na história do Node.js:
- **2009**: O Node.js é introduzido por Ryan Dahl.
- **2010**: npm (Node Package Manager) é lançado, aumentando ainda mais a popularidade do Node.js.
- **2015**: A Fundação Node.js é formada, supervisionando o desenvolvimento do Node.js.
- **2018**: O Node.js 10 se torna a versão de Suporte a Longo Prazo (LTS), introduzindo melhorias significativas.

---

### Node.js vs Navegador

Embora o Node.js e o navegador usem JavaScript, eles servem a propósitos diferentes e têm ambientes distintos:

1. **Objetos Globais**:
   - **Navegador**: `window`, `document`, `navigator`, etc.
   - **Node.js**: `global`, `process`, `require`, etc.

2. **Módulos**:
   - **Navegador**: Módulos ES (usando `import/export`).
   - **Node.js**: CommonJS (usando `require/module.exports`) e também suporta Módulos ES.

3. **APIs**:
   - **Navegador**: Manipulação do DOM, API `fetch` para requisições HTTP.
   - **Node.js**: Acesso ao sistema de arquivos (`fs`), comunicação de rede (`http`, `net`), entre outros.

4. **Ambiente de Execução**:
   - **Navegador**: Ambiente isolado para interação com a interface do usuário.
   - **Node.js**: Ambiente de linha de comando, tipicamente para operações do lado do servidor.

**Exemplo:**

```javascript
// Ambiente de Navegador: Buscando dados de uma API
fetch('https://api.exemplo.com/dados')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Erro:', error));

// Ambiente Node.js: Lendo um arquivo do sistema de arquivos
const fs = require('fs');

fs.readFile('dados.json', 'utf8', (err, data) => {
  if (err) {
    console.error('Erro:', err);
    return;
  }
  console.log(JSON.parse(data));
});
```

---

### Executando Código Node.js

Para executar código Node.js, você precisará ter o Node.js instalado em sua máquina. Você pode baixá-lo e instalá-lo a partir de [nodejs.org](https://nodejs.org/).

**Passos para executar código Node.js:**

1. Crie um novo arquivo com a extensão `.js`, por exemplo, `app.js`.
2. Escreva seu código JavaScript no arquivo.
3. Abra seu terminal ou prompt de comando.
4. Navegue até o diretório que contém seu arquivo.
5. Execute o arquivo usando o comando: `node app.js`.

**Exemplo:**

```bash
$ node app.js
```

Se `app.js` contiver um simples `console.log('Olá, Node.js!')`, executar o comando acima produzirá a seguinte saída:

```
Olá, Node.js!
```

---

Este README fornece uma introdução ao Node.js e seus conceitos principais. Com esta base, você está pronto para explorar a ampla gama de possibilidades que o Node.js oferece, desde a construção de servidores até a criação de ferramentas de linha de comando. Feliz codificação!
