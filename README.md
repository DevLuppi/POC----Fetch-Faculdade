# POC----Fetch

Este projeto demonstra o uso da Fetch API em JavaScript para realizar requisições HTTP e manipular respostas de forma assíncrona. O exemplo faz uma requisição para uma API pública e exibe uma lista de usuários.

Funcionalidades
Realizar uma requisição HTTP GET para uma API externa.
Converter a resposta HTTP em formato JSON.
Exibir os dados recebidos na página.
Tratamento de erros em caso de falha na requisição.
Tecnologias Utilizadas
HTML: Para a estrutura básica da página.
JavaScript (Fetch API): Para fazer requisições HTTP e manipular dados de forma assíncrona.
Requisitos
Para rodar o projeto, você só precisa de um navegador moderno que suporte a API fetch() (como Google Chrome, Firefox, ou qualquer versão recente de outros navegadores).

Como Executar
Clone o repositório ou faça o download dos arquivos.

Certifique-se de que os seguintes arquivos estejam no diretório do projeto:

index.html: Arquivo HTML que contém a estrutura da página.
app.js: Arquivo JavaScript que contém a lógica para fazer a requisição e exibir os dados.
Abra o arquivo index.html em um navegador.

Ao abrir a página, a lista de usuários será carregada automaticamente.

Estrutura do Projeto
plaintext
Copiar código
.
├── index.html      # Página HTML
├── app.js          # Script JavaScript contendo a lógica da Fetch API
└── README.md       # Documentação do projeto
Exemplo de Código (app.js)
javascript
Copiar código
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
Conceitos Importantes
1. Fetch API
A fetch() API é uma interface nativa do JavaScript que permite fazer requisições HTTP de forma simples e sem a necessidade de bibliotecas externas como o XMLHttpRequest.

2. Promise
O método fetch() retorna uma Promise, o que significa que ele lida com operações assíncronas. Quando uma requisição é feita, a Promise entra em estado "pendente" e muda para "resolvida" (em caso de sucesso) ou "rejeitada" (em caso de erro).

3. Tratamento de Erros
O tratamento de erros é feito usando o bloco .catch(), que captura qualquer erro ocorrido durante a requisição, como problemas de rede ou respostas não OK (status diferente de 200-299).

Possíveis Melhorias
Adicionar um indicador de carregamento para melhorar a experiência do usuário enquanto os dados são obtidos.
Implementar um botão de "Recarregar" para permitir novas requisições sem recarregar a página.
Usar o async/await para tornar o código assíncrono mais legível.
Licença
Este projeto é de código aberto e pode ser usado livremente para fins educativos ou comerciais.
