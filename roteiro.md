## 1 - Cadastro de Usuários

### 1.1 - Sucesso - Admin True
**Objetivo:** Criar um usuário administrador, validar seus dados, atualizar algum dado e, por fim, deletá-lo.
**Cenário:**
1. Acessar o endpoint de cadastro de usuários.
2. Preencher os campos obrigatórios:
   - Nome
   - Email
   - Senha
   - Marcar a opção "Cadastrar como administrador".
3. Enviar a requisição para o endpoint de administrador (`admin: true`).
4. Validar que o usuário foi criado com sucesso, verificando a resposta da API ou a mensagem na interface.
5. Realizar uma atualização em algum dado do usuário, como o nome ou o email.
6. Validar que a atualização foi realizada com sucesso.
7. Deletar o usuário.
8. Validar que o usuário foi removido do sistema.

### 1.2 - Sucesso - Admin False
**Objetivo:** Criar um usuário comum, validar seus dados e, em seguida, deletá-lo.
**Cenário:**
1. Acessar o endpoint de cadastro de usuários.
2. Preencher os campos obrigatórios:
   - Nome
   - Email
   - Senha
   - **Não** marcar a opção "Cadastrar como administrador".
3. Enviar a requisição para o endpoint de usuário comum (`admin: false`).
4. Validar que o usuário foi criado com sucesso.
5. Deletar o usuário.
6. Validar que o usuário foi removido do sistema.
   
### 1.3 - Falha - Usuários Iguais
**Objetivo:** Garantir que o sistema não permita o cadastro de usuários duplicados.
**Cenário:**
1. Acessar o endpoint de cadastro de usuários.
2. Preencher os campos obrigatórios:
   - Nome
   - Email
   - Senha
   - Marcar a opção "Cadastrar como administrador".
3. Enviar a requisição para o endpoint de administrador (`admin: true`).
4. Validar que o usuário foi criado com sucesso.
5. Tentar criar um novo usuário com o mesmo email e senha utilizados anteriormente.
6. Validar que a criação falhou e que a mensagem de erro "Este email já está sendo usado" foi exibida.

## 2 - Login

### 2.1 - Login de Sucesso
**Objetivo:** Realizar login com credenciais válidas.
**Cenário:**
1. Criar um usuário com nome, email e senha.
2. Acessar a página de login.
3. Preencher os campos obrigatórios:
   - Email
   - Senha
4. Enviar a requisição de login com os dados corretos.
5. Validar que o login foi realizado com sucesso e que o usuário foi autenticado corretamente.

### 2.2 - Login Inválido
**Objetivo:** Validar que o sistema não permite login com credenciais inválidas.
**Cenário:**
1. Criar um usuário com nome, email e senha.
2. Acessar a página de login.
3. Preencher os campos obrigatórios com dados inválidos ou inexistentes:
   - Email incorreto
   - Senha incorreta
4. Enviar a requisição de login com dados incorretos.
5. Validar que o sistema exibe a mensagem de erro "Email e/ou credenciais inválidas" e impede o login.

## 3 - Criando Produtos

### 3.1 - Criar Produtos com Sucesso
**Objetivo:** Criar um novo produto, validar seus dados, atualizar as informações e deletá-lo.
**Cenário:**
1. Cadastrar um novo usuário.
2. Realizar o login com o novo usuário.
3. Acessar a página de criação de produtos.
4. Preencher os campos obrigatórios para criar um produto:
   - Nome do produto
   - Preço
   - Descrição
   - Quantidade
5. Enviar a requisição para o endpoint de criação de produtos.
6. Validar que o produto foi criado com sucesso.
7. Atualizar algum dado do produto, como o nome ou o preço.
8. Validar que a atualização foi realizada corretamente.
9. Deletar o produto.
10. Validar que o produto foi removido do sistema.
11. Deletar o usuário criado no início do processo.

### 3.2 - Produtos Repetidos
**Objetivo:** Garantir que o sistema não permita a criação de produtos com nomes duplicados.
**Cenário:**
1. Cadastrar um novo usuário.
2. Realizar o login com o novo usuário.
3. Acessar a página de criação de produtos.
4. Preencher os campos obrigatórios para criar um produto:
   - Nome do produto
   - Preço
   - Descrição
   - Quantidade
5. Enviar a requisição para o endpoint de criação de produtos e validar que o produto foi criado com sucesso.
6. Tentar criar um novo produto com o mesmo nome do produto anterior.
7. Validar que a criação falhou e que a mensagem de erro "Já existe produto com esse nome" foi exibida.
8. Deletar o produto criado anteriormente.
9. Deletar o usuário criado no início do processo.

## 4 - Testes de Carrinho

### 4.1 - Compra Feita com Sucesso
**Objetivo:** Realizar uma compra com sucesso, validando o estoque após a conclusão.
**Cenário:**
1. Criar um novo usuário.
2. Realizar login com o usuário criado.
3. Criar 2 produtos novos no sistema.
4. Adicionar os produtos ao carrinho e concluir a compra.
5. Verificar o estoque dos produtos após a compra, validando que a quantidade foi atualizada corretamente.
6. Deletar os 2 produtos criados.
7. Deletar o usuário.

### 4.2 - Cancelar Compra
**Objetivo:** Cancelar uma compra antes de sua conclusão.
**Cenário:**
1. Criar um novo usuário.
2. Realizar login com o usuário criado.
3. Criar 2 produtos novos no sistema.
4. Adicionar os produtos ao carrinho, mas cancelar a compra antes de finalizá-la.
5. Verificar que os produtos continuam no estoque e a compra não foi concluída.
6. Deletar os 2 produtos criados.
7. Deletar o usuário.

### 4.3 - Falha ao Comprar, Token de Usuário Expirado
**Objetivo:** Simular uma falha de compra devido à expiração do token de autenticação.
**Cenário:**
1. Criar um novo usuário.
2. Realizar login com o usuário criado.
3. Criar 2 produtos novos no sistema.
4. Aguardar 10 minutos após o login para que o token expire.
5. Tentar concluir a compra após a expiração do token.
6. Verificar que a mensagem "Token de acesso ausente, inválido, expirado ou usuário do token não existe mais" foi exibida.
7. Deletar os 2 produtos criados.
8. Deletar o usuário.

### 4.4 - Deletar Usuário com Carrinho Vazio
**Objetivo:** Tentar deletar um usuário sem produtos no carrinho e verificar a resposta.
**Cenário:**
1. Criar um novo usuário.
2. Realizar login com o usuário criado.
3. Tentar concluir uma compra sem adicionar produtos ao carrinho.
4. Verificar que a mensagem "Não foi encontrado carrinho para esse usuário" é exibida.
5. Deletar o usuário.
