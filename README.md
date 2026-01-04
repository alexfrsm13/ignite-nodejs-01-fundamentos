<p align="center">
  <img alt="Formação Node.js" src="https://storage.googleapis.com/star-lab/novo-site/formacoes/nodejs/node-icon.svg" width="100px" />
</p>

# 🚀 Ignite Node.js Fundamentos

> API desenvolvida inteiramente com **Node.js puro** (sem frameworks), focada na compreensão profunda de **Streams**, **Buffers** e do **Protocolo HTTP**, utilizando um CRUD de usuários como base.

## 💻 Sobre o Projeto

Esta aplicação é uma API de gerenciamento de usuários que permite criar, listar, atualizar e remover registros.

Porém, o objetivo real deste projeto vai muito além do CRUD. Ele foi construído para desmistificar a "caixa preta" dos frameworks (como Express ou NestJS), implementando manualmente:
- **Body Parsing:** Leitura de dados via Streams e montagem de Buffers.
- **Roteamento Dinâmico:** Uso de Regex para interpretar URLs e parâmetros (`:id`).
- **Banco de Dados em Arquivo:** Persistência local simulando um banco de dados real.

Além da API, o projeto contém arquivos de estudo isolados (`fundamentals.js`, `fake-upload...`) que demonstram o poder das **Streams** para processamento de dados sob demanda.

## 🛠 Tecnologias Utilizadas

- **Node.js** (Runtime)
- **JavaScript** (ESModules)
- **Módulos Nativos:**
  - `node:http`: Criação do servidor web.
  - `node:stream`: Manipulação de fluxos de leitura, escrita e transformação.
  - `node:fs/promises`: Manipulação de arquivos (Banco de dados JSON).
  - `node:crypto`: Geração de UUIDs e criptografia.

## ⚙️ Arquitetura e Estrutura

O projeto foi organizado para separar responsabilidades, mesmo sem usar bibliotecas externas:

| Arquivo | Responsabilidade |
|---|---|
| `server.js` | Inicialização do servidor e composição dos middlewares. |
| `routes.js` | Definição das rotas de Usuários (`/users`) e seus handlers. |
| `database.js` | Classe responsável pela persistência dos dados no arquivo `db.json`. |
| `json.js` | Middleware que intercepta a stream de requisição e formata o Body para JSON. |
| `build-route-path.js` | Utilitário que converte rotas (ex: `/users/:id`) em **Regex**. |
| `fundamentals.js` | Arquivo de estudo prático sobre conceitos de Streams (Readable/Writable/Transform). |

## 🔌 Rotas da API

### Usuários (`/users`)

| Método | Rota | Descrição |
|---|---|---|
| **POST** | `/users` | Cria um novo usuário. |
| **GET** | `/users` | Lista usuários. Aceita filtro de busca por nome ou email (ex: `?search=Alex`). |
| **PUT** | `/users/:id` | Atualiza os dados de um usuário (Nome e Email). |
| **DELETE** | `/users/:id` | Remove um usuário do banco de dados. |

### 📝 Exemplos de Requisição

#### 1. Criar Usuário (POST)
```json
POST /users
Content-Type: application/json

{
  "name": "Alex Fernando",
  "email": "alex@example.com"
}
```
#### 2. Filtrar Usuários (GET)
```bash
# Busca usuários que contenham "Alex" no nome ou email
GET /users?search=Alex
```

## 🌊 Aprofundamento em Streams

Uma parte essencial deste projeto foi o estudo de **Node.js Streams**. Diferente de trabalhar com dados carregados inteiramente na memória (o que pode travar o servidor com arquivos grandes), as Streams permitem processar dados sob demanda.

Foram criados scripts auxiliares na raiz do projeto para testar esses conceitos na prática:

- **`fundamentals.js`**: Demonstração de *Readable*, *Writable* e *Transform Streams* isoladas.
- **`fake-upload-to-http-stream.js`**: Simula um upload de arquivo pesado enviando dados aos poucos para o servidor.
- **`stream-http-server.js`**: Um servidor HTTP minimalista que processa dados de upload em tempo real.

Para testar os conceitos estudados:

```bash
# Executa o exemplo de Streams fundamentais (leitura/escrita/transformação)
$ node fundamentals.js

# Executa uma simulação de upload via stream
$ node fake-upload-to-http-stream.js
```

## 🚀 Como Executar

### Pré-requisitos
Certifique-se de ter o [Node.js](https://nodejs.org/en/) (versão 18+ recomendada para usar o modo `--watch`) e o [Git](https://git-scm.com) instalados.

### Passo a passo

```bash
# Clone este repositório
$ git clone [https://github.com/alexfrsm13/ignite-nodejs-01-fundamentos](https://github.com/alexfrsm13/ignite-nodejs-01-fundamentos)

# Acesse a pasta do projeto
$ cd ignite-nodejs-01-fundamentos

# Execute o servidor (O parâmetro --watch reinicia ao salvar alterações)
$ node --watch server.js
```
## 🧠 Aprendizados

Este projeto solidificou a base necessária para atuar como Backend Engineer no ecossistema JavaScript:

- **Streams e Buffers:** Compreensão de como o Node.js lida com grandes volumes de dados de forma eficiente e como converter binários (`Chunks`) para JSON.
- **HTTP "Raw":** Entendimento de Status Codes (`201`, `204`, `404`), Headers e Métodos sem abstrações de frameworks.
- **Regex em Rotas:** Como criar um interpretador de rotas dinâmicas do zero para capturar parâmetros como `:id`.
- **Algoritmos de Busca:** Implementação manual de lógica de filtragem via Query Parameters.

## 🦸 Autor

Feito com 💜 por **Alex**.

[![Linkedin Badge](https://img.shields.io/badge/-LinkedIn-blue?style=flat-square&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/alex-fernando-0542aa279/)]([alex-fernando-0542aa279](https://www.linkedin.com/in/alex-fernando-0542aa279/))

## 📝 Licença

Este projeto está sob a licença **MIT**. Veja o arquivo [LICENSE](./LICENSE) para mais detalhes.


```
MIT License

Copyright (c) 2026 Alex Fernando

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
