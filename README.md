# Sistema de Autenticação

Este é um projeto de sistema de autenticação básico desenvolvido em HTML, CSS e JavaScript (usando jQuery) para o frontend, juntamente com uma API RESTful no backend (utilizando CodeIgniter e JWT para autenticação). O sistema permite que os usuários registrem uma conta, façam login e permaneçam autenticados usando JSON Web Tokens (JWT).

## Funcionalidades

- **Registro de Usuário**: Permite que novos usuários se registrem com um e-mail e senha.
- **Login de Usuário**: Autentica o usuário e gera um token JWT, armazenado no `localStorage`.
- **Manter Usuário Logado**: Verifica automaticamente a validade do token ao carregar a página e mantém o usuário logado enquanto o token for válido.
- **Logout de Usuário**: Revoga o token JWT e remove-o do `localStorage`.

## Tecnologias Utilizadas

### Frontend

- **HTML** e **CSS**: Interface do usuário.
- **Bootstrap 5.3**: Design responsivo e estilização.
- **JavaScript (jQuery)**: Manipulação do DOM e requisições AJAX para interações com a API.

### Backend

- **CodeIgniter**: Framework PHP para a API RESTful.
- **JWT (JSON Web Tokens)**: Para autenticação segura dos usuários.

## Instalação e Configuração

### Pré-requisitos

- **Servidor Apache** com PHP (ou outro servidor compatível com PHP).
- **Banco de Dados** (MySQL ou MariaDB recomendado).
- **Composer** (para gerenciar dependências do CodeIgniter).
- **Biblioteca JWT** (instalada via Composer com `firebase/php-jwt`).

### Configuração do Backend

1. Clone o repositório ou baixe os arquivos para o seu servidor.
2. Instale as dependências do projeto:
   ```bash
   composer install
   ```
````

3. Configure o arquivo `.env` com as informações do banco de dados e uma chave secreta para JWT:
   ```
   database.default.hostname = localhost
   database.default.database = seu_banco
   database.default.username = seu_usuario
   database.default.password = sua_senha
   database.default.DBDriver = MySQLi
   JWT_SECRET = 'sua_chave_secreta'
   ```
4. Importe o banco de dados ou crie a tabela de usuários conforme necessário para armazenar as credenciais e tokens.

### Configuração do Frontend

1. Modifique a variável `API_BASE_URL` no arquivo HTML para apontar para o endereço onde a API backend está hospedada. Exemplo:
   ```javascript
   const API_BASE_URL = "http://localhost:8080/";
   ```

## Executando o Projeto

1. Inicie o servidor localmente ou no ambiente configurado.
2. Abra o arquivo HTML no navegador para acessar o sistema de autenticação.

## Estrutura de Arquivos

- **HTML e CSS**: Estrutura e estilo da interface do usuário.
- **JavaScript (jQuery)**: Gerenciamento do estado de autenticação e comunicação com a API.
- **CodeIgniter Controllers**:
  - **AuthController**: Gerencia as operações de autenticação, incluindo `register`, `login`, `verifyToken` e `logout`.
- **Models**:
  - **UserModel**: Modelo do usuário que interage com o banco de dados.
  - **BlacklistedTokenModel**: Modelo que armazena tokens revogados para logout seguro.

## Endpoints da API

- `POST /register`: Registra um novo usuário.
- `POST /login`: Autentica o usuário e gera um token JWT.
- `POST /verify`: Verifica a validade do token JWT.
- `POST /logout`: Revoga o token JWT.

## Uso do Projeto

1. **Registrar**: Clique na aba "Registro" e preencha o formulário de registro. Após o registro, será exibida uma mensagem de sucesso, e o usuário poderá realizar o login.
2. **Login**: Após registrar-se, o usuário pode usar o e-mail e senha para realizar o login. Um token JWT será salvo no `localStorage` e o conteúdo da página será atualizado para mostrar que o usuário está autenticado.
3. **Logout**: Clicando no botão "Sair", o usuário faz logout. O token será revogado e removido do `localStorage`, e o usuário retornará para os formulários de autenticação.

## Mensagens e Notificações

As mensagens de erro e sucesso são exibidas na forma de `toasts` (notificações pop-up) usando Bootstrap.

## Solução de Problemas

- **Problemas com CORS**: Se você encontrar problemas de CORS ao fazer requisições para o backend, verifique se o servidor está configurado para permitir requisições de origem cruzada.
- **Token JWT Expirado**: O token expira após um período (definido no backend). Nesse caso, o usuário será automaticamente deslogado e precisará fazer login novamente.

## Licença

Este projeto está licenciado sob a licença MIT.

```

Esse `README.md` fornece uma visão completa do projeto, incluindo suas funcionalidades, requisitos, instalação e uso.
```
