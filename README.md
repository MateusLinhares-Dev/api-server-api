# Projeto de API de Gerenciamento de Salas

Este projeto consiste em uma API robusta para gerenciar salas, questões e áudio, desenvolvida com foco em escalabilidade e manutenibilidade. Utiliza tecnologias modernas para garantir um ambiente de desenvolvimento eficiente e um deploy simplificado.




## Tecnologias Utilizadas

Este projeto foi construído utilizando as seguintes tecnologias:

- **Node.js**: Ambiente de execução JavaScript.
- **TypeScript**: Linguagem de programação que adiciona tipagem estática ao JavaScript, melhorando a robustez e a manutenibilidade do código.
- **Fastify**: Framework web rápido e de baixo overhead para Node.js, otimizado para construir APIs.
- **Drizzle ORM**: ORM (Object-Relational Mapper) moderno e leve para TypeScript, facilitando a interação com o banco de dados.
- **PostgreSQL (via `postgres` driver)**: Sistema de gerenciamento de banco de dados relacional.
- **Biome**: Ferramenta de formatação e linting para manter a consistência do código.
- **Docker**: Plataforma para desenvolver, enviar e executar aplicações em contêineres, garantindo ambientes consistentes.
- **@google/genai**: Integração com a API Generative AI do Google, possivelmente para funcionalidades de áudio ou questões.




## Configuração

Para configurar e rodar o projeto localmente, siga os passos abaixo:

### 1. Variáveis de Ambiente

Crie um arquivo `.env` na raiz do projeto com as variáveis de ambiente necessárias. Um exemplo mínimo pode incluir:

```
DATABASE_URL="postgres://docker:docker@localhost:5435/agents"
```

### 2. Docker

O projeto utiliza Docker para gerenciar o banco de dados PostgreSQL. Certifique-se de ter o Docker e o Docker Compose instalados em sua máquina.

Para iniciar o serviço de banco de dados, execute o seguinte comando na raiz do projeto:

```bash
docker compose up -d
```

Este comando irá iniciar um contêiner PostgreSQL na porta `5435` e criar o banco de dados `agents` com as configurações iniciais definidas em `./docker/setup.sql`.

### 3. Dependências

Instale as dependências do projeto utilizando o npm ou yarn:

```bash
npm install
# ou
yarn install
```




## Como Rodar a Aplicação

Após configurar o Docker e instalar as dependências, você pode rodar a aplicação utilizando os seguintes scripts:

- **`npm run dev`**: Inicia o servidor de desenvolvimento com `watch` para recarregar automaticamente as alterações no código. Ideal para o desenvolvimento.
- **`npm start`**: Inicia o servidor de produção.
- **`npm run db:generate`**: Gera as migrações do Drizzle ORM com base nas suas definições de schema.
- **`npm run db:migrate`**: Aplica as migrações pendentes ao banco de dados.
- **`npm run db:seed`**: Executa o script de seed do banco de dados para popular com dados iniciais.

### Exemplo de Fluxo de Trabalho

1. Inicie o contêiner Docker do PostgreSQL:
   ```bash
   docker compose up -d
   ```
2. Instale as dependências (se ainda não o fez):
   ```bash
   npm install
   ```
3. Gere e aplique as migrações do banco de dados:
   ```bash
   npm run db:generate
   npm run db:migrate
   ```
4. (Opcional) Popule o banco de dados com dados de exemplo:
   ```bash
   npm run db:seed
   ```
5. Inicie a aplicação em modo de desenvolvimento:
   ```bash
   npm run dev
   ```

Agora sua API estará rodando e pronta para ser utilizada!