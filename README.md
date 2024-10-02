# POC---Fetch 

Este projeto demonstra o uso da Fetch API em JavaScript para realizar requisições HTTP e manipular respostas de forma assíncrona. O exemplo faz uma requisição para uma API pública e exibe uma lista de usuários.

## Funcionalidades

- Realizar uma requisição HTTP GET para uma API externa.
- Converter a resposta HTTP em formato JSON.
- Exibir os dados recebidos na página.
- Tratamento de erros em caso de falha na requisição.

## Tecnologias Utilizadas

- **HTML**: Para a estrutura básica da página.
- **JavaScript (Fetch API)**: Para fazer requisições HTTP e manipular dados de forma assíncrona.

## Requisitos

Para rodar o projeto, você só precisa de um navegador moderno que suporte a API `fetch()` (como Google Chrome, Firefox, ou qualquer versão recente de outros navegadores).

## Estrutura do Projeto

```plaintext
.
├── index.html      # Página HTML contendo a lógica da Fetch API em Javascript
└── README.md       # Documentação do projeto
```

### Exemplo de Código

```javascript
// URL da API pública de exemplo
const apiUrl = 'https://jsonplaceholder.typicode.com/users';

// Função para buscar dados da API usando fetch()
function fetchUsers() {
  fetch(apiUrl)
    .then(response => {
      if (!response.ok) {
        throw new Error(`Erro: ${response.status}`);
      }
      return response.json();
    })
    .then(data => {
      displayUsers(data);
    })
    .catch(error => {
      console.error('Ocorreu um erro durante a requisição:', error);
      document.getElementById('user-list').innerText = 'Falha ao carregar os usuários.';
    });
}

// Função para exibir a lista de usuários na página
function displayUsers(users) {
  const userList = document.getElementById('user-list');
  users.forEach(user => {
    const userItem = document.createElement('div');
    userItem.innerHTML = `<strong>Nome:</strong> ${user.name}<br><strong>Email:</strong> ${user.email}<br><br>`;
    userList.appendChild(userItem);
  });
}

// Chama a função para buscar e exibir os usuários ao carregar a página
fetchUsers();
```

## Conceitos Importantes

### 1. **Fetch API**
A `fetch()` API é uma interface nativa do JavaScript que permite fazer requisições HTTP de forma simples e sem a necessidade de bibliotecas externas como o `XMLHttpRequest`.

### 2. **Promise**
O método `fetch()` retorna uma *Promise*, o que significa que ele lida com operações assíncronas. Quando uma requisição é feita, a Promise entra em estado "pendente" e muda para "resolvida" (em caso de sucesso) ou "rejeitada" (em caso de erro).

### 3. **Tratamento de Erros**
O tratamento de erros é feito usando o bloco `.catch()`, que captura qualquer erro ocorrido durante a requisição, como problemas de rede ou respostas não OK (status diferente de 200-299).

## Possíveis Melhorias

- Adicionar um indicador de carregamento para melhorar a experiência do usuário enquanto os dados são obtidos.
- Implementar um botão de "Recarregar" para permitir novas requisições sem recarregar a página.
- Usar o `async/await` para tornar o código assíncrono mais legível.
