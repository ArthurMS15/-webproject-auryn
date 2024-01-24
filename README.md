# -webproject-auryn
Desenvolvimento de um formulário de cadastro com validação de dados, utilizando HTML, CSS e Bootstrap. O formulário deve ser implementado com VueJs ou React, e os dados devem ser salvos em um banco de dados usando o framework Symfony no backend.

# Descrição e tempo decorrido (aproximado) das atividades:
- Elementos do Formulário, Viewport, Ajustes de Campo e Tamanho do Container (Estrutura inicial com bootstrap) além daValidação de Dados, Centralização de Logo, Título, Botão de Submissão e Responsividade (verificação de senhas iguais): **1h**;
- Respostas teóricas para Boas Práticas de Comunicação e Usabilidade: **20min**;
- Interação com formulário, renderização de elementos com JavaScript puro, e início de implementação com VueJS: **1h40min**;
- Configuração de ambiente Docker e WSL2: **40min**;
- Implementando Backend (banco de dados) com Symfony: **1h30min**;
- Conectando frontend com backend: **1h10min**;
- Retoques finais (alerta de conta criada com sucesso, verificação de email ja cadastrado, máscara para melhor visualização de data e criptografia de senha (o Symfony utiliza a interface UserPasswordEncoderInterface para realizar a codificação segura da senha do usuário, com bcrypt sendo o algoritmo utilizado)): **1h30min**;

# Exercício: Formulário de Cadastro em HTML. Além de Espaçamentos e Responsividade com Bootstrap

## 1. Estrutura Inicial e Tamanho do Container:

- Crie o arquivo `form.html`.
- Utilize as tags HTML básicas.
- Insira uma `<div>` para o formulário.
- Adicione a imagem da logo e o título do formulário.
- Reduza o *container* em telas grandes.
- Amplie em telas pequenas.

## 2. Elementos do Formulário, Viewport e Ajustes de Campo:

- Crie campos utilizando `<label>` e `<input>` para nome, telefone, data de nascimento, e-mail, senha, confirmação de senha e CPF.
- Configure o viewport.
- Alinhe campos em linhas específicas.
- Ajuste margens, espaçamentos e laterais dos labels.

## 3. Validação de Dados, Centralização de Logo e Título:

- Implemente a validação de dados, incluindo padrões e torne todos os campos obrigatórios.
- Mantenha a logo com 200px.
- Centralize logo e título.
- Adicione espaçamentos adequados.


## 4. Botão de Submissão:

- Crie um botão de submissão com uma nomenclatura clara para melhor usabilidade.


## 5. Margens, Estilos Adicionais:

- Adicione margem superior generosa.
- Defina cor mais clara para texto small.
- Estilize o botão para consistência.
- Utilize a fonte *Work Sans* do Google Fonts.
- Aplique mudanças com folha de estilos em cascata (CSS).

## 6. Testes Responsivos:

- Teste em diferentes telas.

## 7. Interação com formulário e Renderização de elementos, ambos via JS. E implementando VueJs:

- Título auto explicativo.

## 8. Configuração do backend:

- Ambiente de Desenvolvimento Symfony com docker e WSL 2
- Backend/banco de dados implementando com Symfony
- Conectando frontend com backend (Status de carregando e fazer POST para o)