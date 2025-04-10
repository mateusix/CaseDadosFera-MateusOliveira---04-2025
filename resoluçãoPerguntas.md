# Resolução de Perguntas do Case - Analista de Suporte

> Documento com a resolução estruturada das perguntas do case proposto pela Dadosfera, focado em análise de problemas, atendimento ao cliente e boas práticas de suporte.

---






## Pergunta: 4.16.6_ Item Troubleshooting

Imagine que você é um analista de suporte e recebe um chamado de um cliente reportando um problema na importação dos dados da plataforma **Dadosfera**.

**Situação**:
- O erro ocorreu em uma pipeline de coleta de dados.
- Você deve interagir como se estivesse atendendo o cliente, explicando o problema e sugerindo a solução.
- Também é necessário escrever orientações adicionais sobre cuidados ao carregar dados do **Google Sheets** na plataforma.

**Instruções adicionais**:
- Utilize a documentação oficial da Dadosfera para entender e explicar como baixar os logs de execução da pipeline.


---

# Resposta:  
Contexto do Problema

Durante a execução da pipeline de coleta na Dadosfera, foi identificado o seguinte erro nos logs:

`HTTP-error-code: 403`
`Request had insufficient authentication scopes.`
`PERMISSION_DENIED`
# reason: `ACCESS_TOKEN_SCOPE_INSUFFICIENT`


Esse erro indica que o token de acesso utilizado não possui as permissões necessárias para acessar o Google Sheets.

---

## Resposta ao Cliente (Simulação de Atendimento)

Olá! Tudo bem?

Analisando os logs da sua pipeline de coleta, identificamos que o erro está relacionado às permissões do token de acesso ao Google Sheets. O erro retornado foi:

> **"Request had insufficient authentication scopes."**

Isso significa que as credenciais atuais não possuem as autorizações adequadas para acessar a planilha.

### O que você precisa fazer:

1. Acesse o **Connection Manager** da Dadosfera e edite a conexão com o Google Sheets.
2. Atualize ou recrie as credenciais, garantindo que os escopos (permissions) corretos sejam concedidos.
3. Certifique-se de que o token tenha acesso a um dos seguintes escopos:
   - `https://www.googleapis.com/auth/spreadsheets.readonly`
   - `https://www.googleapis.com/auth/spreadsheets`

Se preferir, também é possível gerar um novo token seguindo o fluxo de autenticação da plataforma, garantindo que todas as permissões necessárias sejam aceitas.

---

## Cuidados Importantes ao Carregar Dados do Google Sheets na Dadosfera

- Verifique se a planilha está compartilhada com a conta que gerou o token de autenticação.
- Confirme se o usuário possui permissão de **leitura** na planilha.
- Garanta que os cabeçalhos das colunas sejam **únicos** e não contenham caracteres especiais.
- Evite **células mescladas** ou **fórmulas complexas** que possam gerar inconsistências.
- Mantenha o **token de autenticação atualizado** para evitar problemas de expiração ou escopo insuficiente.

---

## Como Baixar os Logs de Execução na Dadosfera

Para baixar os logs de execução de uma pipeline:

1. Acesse a aba do **Job/Pipeline** correspondente.
2. Clique em **"Ver Logs"**.
3. Utilize a opção **"Exportar"** para salvar os logs localmente.

---







## Pergunta: 4.16.7_ tem Processos Internos-

- A Dadosfera está passando por um upgrade no seu sistema de gerenciamento de usuários, incorporando:
  - **SSO (Single Sign-On)**;
  - **Gerenciamento de ciclo de vida do usuário**;
  - **Novo diretório em nuvem**.
- Existe um impacto potencial em integrações existentes, especialmente em pipelines de coleta de dados usando **Google Sheets**.

Você deve interagir como se estivesse atendendo o cliente, explicando:

- O motivo da mudança e seus benefícios.
- Como isso pode impactar o funcionamento atual da pipeline de coleta.
- As ações que o cliente deve tomar para garantir a continuidade dos processos.

**Importante**: Utilize a documentação oficial da Dadosfera para instruir o cliente sobre:

- Como baixar os **logs de execução** da pipeline.
- Quais cuidados devem ser tomados ao **carregar dados do Google Sheets** na plataforma após a mudança.

---

# Resposta:

### 1. Explicação ao Cliente (Tom de Atendimento)

- Informar sobre a atualização de forma clara e acolhedora.
- Explicar o que muda tecnicamente para ele.

### 2. Relação com o Erro 403 (Pipelines)

- Explicar que o erro pode estar relacionado a mudanças no modelo de autenticação e integração.

### 3. Orientações Técnicas

- Como baixar **logs da pipeline** para diagnóstico:
  - Exemplo baseado na documentação Dadosfera: **Acesse a página da pipeline > Aba "Execuções" > Clique em "Baixar logs"**.
- Cuidados específicos ao configurar **Google Sheets**:
  - Revalidar conexões OAuth.
  - Verificar permissões de compartilhamento da planilha.
  - Atualizar credenciais no Connection Manager.

### 4. Plano de Comunicação com a Base de Clientes

- Etapas de preparação.
- Como garantir uma transição suave.
- Suporte disponível antes, durante e depois do upgrade.

---

## ⚡ Observação

Manter sempre uma linguagem:

- **Clara** (evitar excesso de termos técnicos sem explicação).
- **Empática** (mostrar que estamos aqui para apoiar).
- **Pró-ativa** (já orientar próximas ações).








## Pergunta: 4.16.8_ Item Boas-Práticas de Suporte

Imagine que você tenha acesso a uma ferramenta de **Chatbot com Inteligência Artificial** robusta.
O objetivo é integrá-la à **Dadosfera** para **melhorar a experiência de suporte ao cliente**.
Sua missão é estruturar **como essa IA será implementada**, sempre focando em:

- **Aumentar a satisfação** dos clientes.
- **Melhorar o engajamento** com a plataforma.

Você deverá **desenhar o fluxo de atendimento**, detalhando a interação entre:

- **Usuário**.
- **Máquina (IA)** (ex.: GPT, Bard, etc.).
- **Documentação oficial** (docs.dadosfera.ai).
- **Suporte humano** (Equipe Dadosfera).

Além disso, **exemplifique**:

- Um **prompt** feito pelo cliente.
- A **resposta gerada pela IA**.

# Resposta:  

## Estratégia de Implementação

1. **Integração da IA**  
Conectar um chatbot (como ChatGPT ou Bard) à plataforma de atendimento da Dadosfera.

2. **Conexão com a Base de Conhecimento**  
Integrar a IA com a base de documentação disponível no [docs.dadosfera.ai](https://docs.dadosfera.ai).

3. **Definição de Fluxos de Atendimento**  
Configurar fluxos de atendimento que priorizem respostas automáticas e encaminhem para humanos apenas em casos complexos.

4. **Treinamento Contínuo**  
Treinar a IA com perguntas frequentes (FAQs), procedimentos internos e novos aprendizados do time de suporte.

## Fluxo do Processo de Atendimento

- Usuário inicia o contato pelo chat.
- A IA identifica a intenção da pergunta.
  - Se for uma dúvida simples:
    - A IA busca a resposta na documentação (`docs.dadosfera.ai`).
    - A IA responde o usuário.
  - Se for uma dúvida complexa:
    - A IA encaminha o atendimento para um humano do suporte.
    - O suporte humano responde e, se necessário, atualiza a documentação para futuras consultas.

## Exemplo de Prompt e Resposta da IA

**Usuário:**

> Como configurar um novo conector no Dadosfera?

**Resposta da IA:**

> Olá! 👋  
> Para configurar um novo conector no Dadosfera, siga estes passos:
> 
> 1. Acesse seu Painel de Administração.
> 2. Vá para a seção **Conectores** > **Novo Conector**.
> 3. Escolha o tipo de fonte de dados que deseja conectar.
> 4. Preencha as credenciais solicitadas.
> 5. Clique em **Testar Conexão** e depois em **Salvar**.
> 
> Você também pode acessar o passo a passo completo em nossa documentação oficial: [Guia de Conectores - docs.dadosfera.ai](https://docs.dadosfera.ai/conectores).
> 
> Se precisar de ajuda adicional, estou aqui para transferir você para um especialista! 

## Benefícios Esperados

- Atendimento automatizado e rápido para dúvidas comuns.
- Redução no volume de tickets simples.
- Foco do suporte humano em problemas complexos.
- Base de conhecimento atualizada continuamente.
- Aumento da satisfação e retenção de clientes.









