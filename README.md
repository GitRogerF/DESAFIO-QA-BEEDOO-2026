# DESAFIO-QA-BEEDOO-2026
Desafio de QA – Análise de testes para o módulo do curso

## 1. Objetivo da aplicação

A aplicação tem como objetivo permitir o gerenciamento de cursos, possibilitando que usuários realizem o cadastro de novos cursos e visualizem os cursos cadastrados em uma listagem.

O sistema permite registrar informações relevantes sobre os cursos, como:
- Nome do curso
- Descrição do curso
- Instrutor
- Datas de início e fim
- Número de vagas
- Tipo de curso
- URL da imagem de capa
- Endereço (caso seja presencial) ou link de inscrição (caso seja online)

---

## 2. Principais fluxos da aplicação

### Cadastro de cursos
Fluxo onde o usuário acessa a aba "Cadastrar cursos" e preenche um formulário contendo as informações do curso. Após preencher o formulário, o usuário pode cadastrar o curso no sistema.

### Listagem de cursos
Fluxo onde o usuário acessa a aba "Listar cursos", na qual são exibidos os cursos previamente cadastrados, incluindo suas informações e imagem de capa.

---

## 3. Pontos críticos para teste

- Validação de campos obrigatórios no cadastro de cursos
- Validação do formato da URL da imagem
- Validação das datas de início e fim do curso
- Integridade das informações exibidas na listagem de cursos
- Comportamento do sistema ao receber dados inválidos ou incompletos

Durante os testes exploratórios, foi observado que o sistema permite o cadastro de cursos mesmo quando alguns campos importantes não são preenchidos ou possuem valores inválidos (nome do curso, datas, URL da imagem), gerando inconsistências nos dados cadastrados.

---

## 4. Registro de bugs encontrados

### 1. Cadastro sem campos obrigatórios
- **Passos para reproduzir:** Acessar aba "Cadastrar Cursos" e clicar em cadastrar sem preencher nenhum campo.
- **Resultado atual:** Curso cadastrado com sucesso; campos vazios aparecem na listagem.
- **Resultado esperado:** O sistema deveria impedir o cadastro e exibir mensagem informando os campos obrigatórios.
- **Severidade/Impacto:** Alta – possibilidade de registro de dados incompletos.
  
### 2. Cadastro sem data de início
- **Passos:** Deixar o campo de data de início vazio e tentar cadastrar.
- **Resultado atual:** Cadastro realizado, campo vazio na listagem.
- **Resultado esperado:** Cadastro impedido, mensagem de campo obrigatório.
- **Severidade/Impacto:** Alta – dados do curso incompletos.

### 3. Cadastro sem data de fim
- **Passos:** Deixar o campo de data de fim vazio e tentar cadastrar.
- **Resultado atual:** Cadastro realizado, campo vazio na listagem.
- **Resultado esperado:** Cadastro impedido, mensagem de campo obrigatório.
- **Severidade/Impacto:** Alta – período do curso indefinido.

### 4. Data de início maior que data de fim
- **Passos:** Inserir data de início posterior à data de fim e cadastrar.
- **Resultado atual:** Cadastro permitido, datas inconsistentes na listagem.
- **Resultado esperado:** Validação de datas, impedir cadastro.
- **Severidade/Impacto:** Alta – inconsistência cronológica.

### 5. URL de imagem inválida aceita
- **Passos:** Inserir URL de imagem inválida e cadastrar.
- **Resultado atual:** Cadastro permitido; imagem quebrada na listagem.
- **Resultado esperado:** Validação de URL, impedir cadastro.
- **Severidade/Impacto:** Média – impacto visual.

### 6. Exclusão de curso não remove item
- **Passos:** Clicar em "Excluir Curso" na listagem.
- **Resultado atual:** Mensagem de sucesso exibida, mas curso permanece.
- **Resultado esperado:** Curso removido da listagem.
- **Severidade/Impacto:** Alta – funcionalidade de exclusão falha.

### 7. Quebra de layout com descrição extensa
- **Passos:** Inserir descrição com ~5000 caracteres e cadastrar.
- **Resultado atual:** Cadastro realizado; listagem apresenta layout quebrado (imagem desproporcional).
- **Resultado esperado:** Limite de caracteres respeitado ou mensagem de erro.
- **Severidade/Impacto:** Média – problema visual.

---

## 5. Possíveis melhorias

- Implementar validação de campos obrigatórios no cadastro de cursos
- Validar URL da imagem de capa
- Validar datas de início e fim (inclusive para datas futuras)
- Permitir edição de cursos após cadastro
- Validar limite de caracteres da descrição para evitar quebra de layout
- Mostrar endereço ou link do curso na listagem

---

## 6. Evidências

As evidências de cada caso de teste estão disponíveis na pasta [Evidências](./Evidências) deste repositório.