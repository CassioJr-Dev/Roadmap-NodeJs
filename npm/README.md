# npm no Node.js

## Índice
- [Introdução ao npm](#introdução-ao-npm)
- [Instalando Pacotes](#instalando-pacotes)
  - [Instalação Global](#instalação-global)
  - [Instalação Local](#instalação-local)
- [Criando Pacotes](#criando-pacotes)
  - [Pacotes Privados](#pacotes-privados)
  - [Pacotes Públicos](#pacotes-públicos)
- [npx](#npx)
- [Atualizando Pacotes](#atualizando-pacotes)
- [Usando Pacotes Instalados](#usando-pacotes-instalados)
- [Executando Scripts](#executando-scripts)
- [npm Workspaces](#npm-workspaces)

## Introdução ao npm
`npm` (Node Package Manager) é um gerenciador de pacotes para JavaScript, usado principalmente para gerenciar dependências em projetos Node.js. Ele vem incluído com o Node.js e permite que os desenvolvedores instalem, compartilhem e gerenciem módulos de código.

## Instalando Pacotes

### Instalação Global
A instalação global é usada quando você deseja que um pacote esteja disponível em todo o sistema. Isso significa que o pacote pode ser executado de qualquer diretório na sua máquina.

```bash
npm install -g <nome-do-pacote>
```

Exemplo:
```bash
npm install -g nodemon
```
Isso instala o `nodemon` globalmente, permitindo que você o use em qualquer projeto sem precisar instalá-lo localmente.

### Instalação Local
A instalação local instala um pacote no diretório do projeto atual. O pacote é adicionado à pasta `node_modules` e está acessível apenas dentro desse projeto.

```bash
npm install <nome-do-pacote>
```

Exemplo:
```bash
npm install express
```
Isso instala o `express` localmente para o seu projeto, e ele será listado no arquivo `package.json` em `dependencies`.

## Criando Pacotes

### Pacotes Privados
Pacotes privados são usados dentro de uma organização e não estão disponíveis publicamente no registro npm. Eles exigem uma conta npm com acesso a pacotes privados.

Para criar um pacote privado:
1. Certifique-se de que o arquivo `package.json` tenha `"private": true`.
2. Publique o pacote usando:
   ```bash
   npm publish --access restricted
   ```

### Pacotes Públicos
Pacotes públicos estão disponíveis para que qualquer pessoa os instale a partir do registro npm. Por padrão, os pacotes são públicos, a menos que especificado de outra forma.

Para criar um pacote público:
1. Certifique-se de que o `package.json` não tenha `"private": true`.
2. Publique o pacote usando:
   ```bash
   npm publish
   ```

## npx
`npx` é uma ferramenta que vem com o npm (versão 5.2.0 e posteriores) e permite que você execute pacotes diretamente sem instalá-los globalmente.

Exemplo:
```bash
npx create-react-app my-app
```
Este comando cria um novo aplicativo React sem instalar o pacote `create-react-app` globalmente.

## Atualizando Pacotes
Manter seus pacotes atualizados é importante para a segurança e funcionalidade. Você pode atualizar todos os seus pacotes executando:

```bash
npm update
```

Para atualizar um pacote específico:
```bash
npm update <nome-do-pacote>
```

Para atualizar pacotes para a versão mais recente, independentemente das restrições de versão no `package.json`:
```bash
npm install <nome-do-pacote>@latest
```

## Usando Pacotes Instalados
Depois que um pacote é instalado, ele pode ser usado no seu projeto Node.js por meio do `require` ou `import`.

Exemplo:
```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Olá, Mundo!');
});

app.listen(3000, () => {
  console.log('Servidor rodando na porta 3000');
});
```

## Executando Scripts
Scripts são comandos definidos na seção `scripts` do arquivo `package.json`. Eles podem automatizar tarefas como iniciar um servidor, executar testes ou construir seu projeto.

Exemplo da seção de scripts em um `package.json`:
```json
{
  "scripts": {
    "start": "node index.js",
    "test": "mocha"
  }
}
```

Para executar um script, use:
```bash
npm run <nome-do-script>
```

Exemplo:
```bash
npm run start
```

## npm Workspaces
`npm workspaces` é um recurso que permite gerenciar vários pacotes dentro de um único repositório. É útil para monorepos, onde você tem um projeto dividido em diferentes pacotes ou módulos.

### Configurando um Workspace
1. No `package.json` raiz, adicione a chave `workspaces`:
   ```json
   {
     "workspaces": ["packages/*"]
   }
   ```

2. Crie pastas separadas para cada pacote dentro do diretório `packages`.

3. Cada pacote deve ter seu próprio `package.json`.

### Instalando Dependências em Workspaces
Execute o seguinte comando para instalar dependências para todos os pacotes dentro do workspace:
```bash
npm install
```

Isso vinculará as dependências entre seus pacotes, permitindo que compartilhem dependências onde aplicável.

### Executando Scripts em Workspaces
Você pode executar scripts em todos os workspaces simultaneamente ou em um workspace específico.

Para executar um script em todos os workspaces:
```bash
npm run <nome-do-script> --workspaces
```

Para executar um script em um workspace específico:
```bash
npm run <nome-do-script> --workspace=<nome-do-pacote>
```

---

Este README fornece uma visão geral abrangente sobre o `npm` no Node.js, ajudando você a entender como gerenciar dependências, criar pacotes e utilizar os recursos poderosos do npm, como workspaces.
