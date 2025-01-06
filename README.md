### Todo-App 🖥️ 📝

Este projeto foi desenvlvido como teste sobre as competências de Docker e Dockerfile da Trybe.
As alterações desenvolvidas estão nos arquivos Dockerfile e os arquivos command(numero do requisito). 

Olá! Esse é o aplicativo de tarefas **Todo-App**!

Com ele, você pode se organizar de maneira simples, adicionando, marcando e/ou removendo suas tarefas.

![Alt Text](./intro.gif)

#### Requisitos

- [NodeJS LTS](https://github.com/nodesource/distributions/blob/master/README.md#debinstall) (14 ou mais).
  - O Sistema Operacional [deve suportar o NodeJS](https://github-com.translate.goog/nodejs/build/issues/2168?_x_tr_sl=en&_x_tr_tl=pt&_x_tr_hl=pt-BR&_x_tr_pto=nui).
  - Aplicações como o `create-react-app` [requerem essa versão mínima](https://pt-br.reactjs.org/docs/create-a-new-react-app.html#create-react-app) para funcionar corretamente


#### Instalação

Esse é um aplicativo em [NodeJS](https://nodejs.org/pt-br/about/), que possui **dois componentes principais** (`front` e `back`) e um **teste de saúde da aplicação**:
- `Front-end` Essa aplicação consome nossa API e nos retorna nossa lista;
- `Back-end` Onde a **mágica** acontece! Nosso back-end possui um banco de dados interno, onde são salvas nossas tarefas;
- `Testes` Onde validamos a comunicação entre `front` e `back-end`.

##### Estrutura do aplicativo

```bash
todo-app/
├── README.md # este arquivo
├── back-end # responsável por processar nossos dados através de requisições
│   ├── node_modules.tar.gz # pacote opcional, para facilitar a criação de imagens no Docker
│   ├── package.json # principal componente da aplicação
│   ├── package-lock.json # arquivo responsável por otimizar a instalação em outros ambientes
│   └── src
│       ├── api
│       │   ├── routes.js
│       │   └── server.js
│       ├── controllers
│       │   └── Tasks.js
│       ├── database
│       │   ├── tasks.bkp.json
│       │   └── tasks.json
│       ├── models
│       │   └── Tasks.js
│       └── utils
│           └── fileHandler.js
├── front-end # responsável por ser uma interface amigável para nosso back-end
│   ├── node_modules.tar.gz # pacote opcional, para facilitar a criação de imagens no Docker
│   ├── package.json # principal componente da aplicação
│   ├── package-lock.json # arquivo responsável por otimizar a instalação em outros ambientes
│   ├── public
│   │   ├── favicon.ico
│   │   ├── index.html
│   │   ├── logo192.png
│   │   ├── logo512.png
│   │   ├── manifest.json
│   │   └── robots.txt
│   ├── README.md
│   └── src
│       ├── App.css
│       ├── App.js
│       ├── App.test.js
│       ├── components
│       │   ├── ItemAdd
│       │   │   ├── index.jsx
│       │   │   └── styles.css
│       │   ├── ItemList
│       │   │   ├── index.jsx
│       │   │   └── styles.css
│       │   ├── ItemRow
│       │   │   ├── index.jsx
│       │   │   └── styles.css
│       │   └── TaskReset
│       │       └── index.jsx
│       ├── context
│       │   └── taskContext.js
│       ├── index.css
│       ├── index.js
│       ├── logo.png
│       ├── reportWebVitals.js
│       ├── setupTests.js
│       └── utils
│           └── fetch.js
└── tests # responsável por validar essa comunicação
    ├── e2e
    │   └── health_status.test.js
    ├── jest.config.js
    ├── node_modules.tar.gz # pacote opcional, para facilitar a criação de imagens no Docker
    ├── package.json # principal componente da aplicação
    └── package-lock.json # arquivo responsável por otimizar a instalação em outros ambientes
```

###### Instalando o back-end

- Acesse a pasta `./todo-app/back-end`;
- Instalar a aplicação utilizando o comando `npm install`;
- O processo não deve retornar erros. `Warns` *(Avisos)* não impedem seu funcionamento;
- Rodar a aplicação com `npm start`;
- Por padrão, essa aplicação funciona a partir da porta `3001`;

###### Instalando o front-end

- Acesse a pasta `./todo-app/front-end`;
- Instalar a aplicação utilizando o comando `npm install`;
- O processo não deve retornar erros. `Warns` *(Avisos)* não impedem seu funcionamento;
- Rodar a aplicação com `npm start`;
- Esse aplicativo requer, **excepcionalmente**, um arquivo `.env`, já contido em sua pasta no repositório;
- Por padrão, essa aplicação funciona a partir da porta `3000`;
- Essa aplicação pode receber variáveis de ambiente para mudar o acesso do `back-end`:
  - `REACT_APP_API_HOST`: padrão `localhost`;
    - *(Docker)* Aqui você deve indicar o nome do container do `back-end`;
  - `REACT_APP_API_PORT`: padrão `3001`.
    - *(Docker)* Aqui você deve indicar a porta que você definiu internamente no container do `back-end`;

###### Utilizando o aplicativo de testes

- ⚠️ Essa aplicação só funciona **se associada a uma rede Docker**;
- Acesse a pasta `./todo-app/front-end`;
- Instalar a aplicação utilizando o comando `npm install`;
- O processo não deve retornar erros. `Warns` *(Avisos)* não impedem seu funcionamento;
- Rodar a aplicação com `npm test`;
- Essa aplicação pode receber variáveis de ambiente para mudar o acesso ao front-end:
  - `FRONT_HOST`: padrão `localhost`;
    - *(Docker)* Aqui você deve indicar o nome do container do `front-end`;
  - `FRONT_PORT`: padrão `3000`.
    - *(Docker)* Aqui você deve indicar a porta que você definiu internamente no container do `front-end`;
