# 📋 TODO - Lista de Erros e Tarefas

> **Sistema de rastreamento de problemas e tarefas**
> Gerenciado pelo agente TODO Manager

---

## 📊 Resumo

- 🔴 Pendentes: 13
- 🟡 Em andamento: 0
- 🟢 Resolvidos: 0

---

## 📝 Itens

## ❌ Falha de conexão com servidor ao finalizar venda

**Data:** 06/02/2026
**Categoria:** 🏢 Atendimento / 💾 Sistema
**Prioridade:** Alta
**Status:** 🔴 Pendente

**Descrição:**
Ao finalizar uma venda, o sistema apresenta erro de "Falha de conexão com servidor", impedindo a conclusão do processo de venda.

**Impacto:**

- Impossibilidade de finalizar vendas
- Bloqueio da operação comercial
- Possível perda de vendas e insatisfação de clientes

**Ações necessárias:**

- [ ] Verificar status e disponibilidade do servidor
- [ ] Analisar logs de conexão no momento do erro
- [ ] Verificar configurações de rede e timeout da requisição
- [ ] Reproduzir problema em ambiente de testes
- [ ] Aplicar correção (reconexão automática, ajuste de timeout, etc.)
- [ ] Validar correção em produção

---

## ❌ Tela não atualiza ao alterar quantidade pelo atalho Ctrl+Q

**Data:** 06/02/2026
**Categoria:** 🐛 Bug / 🏢 Atendimento
**Prioridade:** Média
**Status:** 🔴 Pendente

**Descrição:**
Na tela de Carrinho (Venda), ao utilizar o atalho Ctrl+Q para alterar a quantidade de um item, o valor é alterado internamente mas a tela não é atualizada visualmente. O usuário não consegue ver a mudança refletida sem interação adicional.

**Contexto observado:**

- Tela: Carrinho (Venda #456)
- Item: Agua Mineral 1,5L - Quantidade 3,000 - R$ 16,50
- Veículo: ABC1234 Honda Civic
- Cliente: Possobon Transportes Ltda

**Impacto:**

- Usuário não tem feedback visual da alteração
- Pode causar confusão e erros na quantidade da venda
- Reduz a confiabilidade da interface

**Ações necessárias:**

- [ ] Verificar handler do atalho Ctrl+Q (evento de teclado)
- [ ] Verificar se o state/reatividade está sendo atualizado corretamente
- [ ] Garantir que o componente do carrinho re-renderiza após alteração de quantidade
- [ ] Testar atualização visual com diferentes métodos de alteração (botões +/-, input direto, Ctrl+Q)
- [ ] Validar correção

---

## ❌ Enter no Alt+Q seleciona bico ao invés de confirmar quantidade

**Data:** 06/02/2026
**Categoria:** 🐛 Bug / 🏢 Atendimento
**Prioridade:** Alta
**Status:** 🔴 Pendente

**Descrição:**
Na tela de Carrinho (Venda), ao usar o atalho Alt+Q, abre o modal "Editar Quantidade" que pede para digitar o número do item. Ao digitar o número e pressionar Enter ("Selecionar"), ao invés de abrir a edição de quantidade do item selecionado, o foco é direcionado para o elemento "bico" no fundo da tela. O fluxo esperado (Alt+Q → selecionar item → editar quantidade) não se completa corretamente.

**Contexto observado (screenshot):**

- Modal: "Editar Quantidade"
- Texto: "Digite o número do item (1 item editável)"
- Campo de input com valor "2"
- Item listado: "1 - Refrigerante Lata 350ml Guara... 1,000"
- Botões: "Cancelar (ESC)" e "Selecionar (Enter)"
- Ao clicar "Selecionar (Enter)", o foco vai para o bico ao invés de prosseguir com a edição

**Impacto:**

- Fluxo de alteração de quantidade fica quebrado
- Operador precisa usar mouse para confirmar, perdendo agilidade
- Causa frustração e lentidão no atendimento

**Ações necessárias:**

- [ ] Verificar callback do botão "Selecionar" no modal "Editar Quantidade"
- [ ] Verificar se o modal fecha corretamente e redireciona o foco para o campo de quantidade do item selecionado
- [ ] Garantir que o Enter no modal não propague para elementos da tela de fundo (bico)
- [ ] Revisar se há validação do número digitado (ex: digitar "2" quando só há 1 item)
- [ ] Testar fluxo completo: Alt+Q → digitar número → Enter → edição de quantidade → confirmar
- [ ] Validar correção

---

## ❌ Erro na transmissão de NFC-e ao finalizar venda

**Data:** 06/02/2026
**Categoria:** 🌐 Integração / 📊 Relatórios
**Prioridade:** Alta
**Status:** 🔴 Pendente

**Descrição:**
Ao finalizar uma venda, o Gerenciador de Documento Fiscal apresenta erro "Erro na Transmissao - Erro ao emitir documento fiscal", impedindo a emissão da NFC-e. A venda é marcada como FINALIZADA mas o documento fiscal não é transmitido com sucesso à SEFAZ.

**Contexto observado (screenshot):**

- Modal: "Gerenciador de Documento Fiscal"
- Venda #464 | NFC-e | R$ 84,71 | FINALIZADA
- Aba "Erro" ativa com indicador vermelho
- Mensagem: "Erro na Transmissao - Erro ao emitir documento fiscal"
- Opções disponíveis: Atualizar Status, Retransmitir, Contingência
- Nota: "Use Contingência quando a SEFAZ estiver indisponível para liberar o cliente"

**Impacto:**

- Documento fiscal não é emitido, gerando pendência fiscal
- Cliente pode ficar aguardando a nota
- Risco de acúmulo de notas não transmitidas
- Possível necessidade de operar em contingência

**Ações necessárias:**

- [ ] Verificar disponibilidade da SEFAZ no momento do erro
- [ ] Analisar logs detalhados da transmissão (código de rejeição, motivo)
- [ ] Verificar certificado digital (validade e configuração)
- [ ] Verificar dados do cliente na aba "Cliente" (endereço, CPF/CNPJ, IE)
- [ ] Tentar retransmitir via botão "Retransmitir"
- [ ] Se SEFAZ indisponível, considerar uso de Contingência
- [ ] Validar se o problema é recorrente ou pontual

---

## ❌ Quantidade não é alterada após selecionar item no modal Editar Quantidade (Alt+Q)

**Data:** 06/02/2026
**Categoria:** 🐛 Bug / 🏢 Atendimento
**Prioridade:** Alta
**Status:** 🔴 Pendente

**Descrição:**
Na tela de Carrinho (Venda), ao usar o atalho Alt+Q para editar a quantidade de um item, o modal "Editar Quantidade" abre corretamente e lista os itens disponíveis. Porém, ao digitar o número do item e pressionar Enter ("Selecionar"), a quantidade do item não é alterada. O fluxo não prossegue para o passo de digitação da nova quantidade.

**Contexto observado (screenshot):**

- Modal: "Editar Quantidade"
- Texto: "Digite o número do item (1 item editável)"
- Campo de input com valor "2"
- Itens listados:
  - Diesel S-10 — 13,390 (combustível, ícone de bico, não editável)
  - 2 - Refrigerante Lata 350ml Guara... — 1,000 (editável)
- Botões: "Cancelar (ESC)" e "Selecionar (Enter)"
- Ao pressionar Enter, a quantidade não é alterada

**Observação:** O modal indica "1 item editável", ou seja, o Diesel S-10 (combustível/bico) não permite edição de quantidade por esse modal. Apenas o item #2 (Refrigerante) é editável. O fluxo deveria: selecionar item → abrir campo para nova quantidade → confirmar.

**Impacto:**

- Operador não consegue alterar quantidade de itens via atalho de teclado
- Obriga uso de outros métodos (botões +/-, input direto) perdendo agilidade
- Fluxo de atendimento rápido fica comprometido

**Ações necessárias:**

- [ ] Verificar se após "Selecionar" o modal abre segundo passo para digitar nova quantidade
- [ ] Verificar lógica de seleção de item (input "2" deve selecionar o Refrigerante)
- [ ] Garantir que o callback de seleção atualiza o state da quantidade e re-renderiza o carrinho
- [ ] Testar fluxo completo: Alt+Q → digitar número do item → Enter → digitar nova quantidade → confirmar
- [ ] Validar correção

---

## ❌ Falha no débito não retorna para seleção de forma de pagamento

**Data:** 06/02/2026
**Categoria:** 🏢 Atendimento / 💾 Sistema
**Prioridade:** Alta
**Status:** 🔴 Pendente

**Descrição:**
Ao finalizar uma venda com pagamento em Débito, quando o cartão do cliente não tem limite suficiente (transação recusada), o sistema permanece na tela de finalização ao invés de retornar para a tela de seleção de forma de pagamento. O operador fica preso na tela de finalizar e não consegue trocar para outra forma de pagamento (Dinheiro, PIX, Crédito, etc.).

**Contexto observado (screenshot):**

- Sistema: I9 PDV - Atendimento
- Venda #468 | Veículo ABC1D23 VW Gol | Cliente: Diego Rodrigues Soares
- Itens: Pipoca Microondas 100g (R$ 3,90) + Gasolina Comum 21,970L (R$ 129,40)
- Total: R$ 133,30
- Pagamento: Débito R$ 133,30 (cartão sem limite)
- Subtotal: R$ 133,30 | Pago: R$ 133,30 | Restante: R$ 0,00
- Botão "Finalizar (F12)" visível
- Formas disponíveis na barra: Dinheiro (F5), PIX (F6), Débito (F7), Crédito (F8), Pontos (F9), Nota Assina (F11)

**Impacto:**

- Operador não consegue trocar a forma de pagamento após recusa do cartão
- Cliente fica aguardando sem solução rápida
- Pode ser necessário cancelar a venda e refazer, causando retrabalho
- Lentidão no atendimento e frustração do operador/cliente

**Ações necessárias:**

- [ ] Verificar tratamento de erro de retorno da operadora de cartão (transação recusada/sem limite)
- [ ] Implementar retorno automático à tela de pagamento quando transação é recusada
- [ ] Permitir que o operador remova o pagamento em débito e selecione outra forma
- [ ] Exibir mensagem clara de "Transação recusada" com opção de tentar novamente ou trocar forma de pagamento
- [ ] Testar fluxo: adicionar débito → recusa → retorno à seleção de pagamento
- [ ] Validar correção

---

## ❌ Busca de motorista por CPF não encontra registro válido

**Data:** 06/02/2026
**Categoria:** 👤 Cadastro / 🏢 Atendimento
**Prioridade:** Alta
**Status:** 🔴 Pendente

**Descrição:**
No modal "Buscar Motorista", ao digitar um CPF válido (com formatação 345.678.901-23) e pressionar "Buscar (Enter)", o sistema retorna "Nenhum motorista encontrado", mesmo sendo um CPF cadastrado no sistema.

**Contexto observado (screenshot):**

- Modal: "Buscar Motorista"
- Campo: "Nome, CPF, Código ou Telefone"
- Valor digitado: 345.678.901-23
- Resultado: "Nenhum motorista encontrado" (texto em vermelho)
- Botões: "Buscar (Enter)" e "Novo Motorista (F3)"
- Atalhos: ESC fechar | ↑↓ navegar | ENTER selecionar | F3 cadastrar

**Impacto:**

- Impossibilidade de vincular motorista à venda por CPF
- Operador precisa buscar por nome ou código, perdendo agilidade
- Pode causar erros na identificação do motorista
- Atraso no atendimento

**Ações necessárias:**

- [ ] Verificar se a busca por CPF está tratando a máscara (pontos e traço) corretamente
- [ ] Testar busca com CPF sem formatação (34567890123) e com formatação (345.678.901-23)
- [ ] Verificar query de busca no backend (se faz LIKE ou match exato)
- [ ] Garantir que o campo CPF no banco de dados está no mesmo formato da busca
- [ ] Testar busca por nome, código e telefone para comparação
- [ ] Validar correção

---

## ❌ Vendedor sem permissão para cadastrar motorista (Acesso negado)

**Data:** 06/02/2026
**Categoria:** 🔐 Autenticação / 🏢 Atendimento
**Prioridade:** Alta
**Status:** 🔴 Pendente

**Descrição:**
No modal "Cadastro Rápido de Motorista", ao preencher os dados e tentar salvar, o sistema exibe mensagem de erro "Acesso negado. Nível mínimo necessário: GERENTE_UNIDADE". Vendedores/operadores do PDV não conseguem cadastrar novos motoristas durante o atendimento, mesmo que o fluxo de venda exija esse cadastro.

**Contexto observado (screenshot):**

- Modal: "Cadastro Rápido de Motorista"
- Nome Completo: Ryan Costa Cunha
- CPF: 529.982.247-25 (validado com ícone verde ✅)
- Celular: (81) 99999-7777
- Erro: "Acesso negado. Nível mínimo necessário: GERENTE_UNIDADE" (texto em vermelho)
- Botão: "Salvar Motorista (Enter)"
- Atalhos: ESC fechar | ENTER avançar campo

**Impacto:**

- Vendedor não consegue cadastrar motorista durante o atendimento
- Necessita chamar gerente para uma operação simples, causando atraso
- Bloqueia o fluxo de venda quando motorista não está cadastrado
- Reduz autonomia do operador e agilidade no atendimento

**Ações necessárias:**

- [ ] Revisar regras de permissão para cadastro rápido de motorista
- [ ] Avaliar se o nível "VENDEDOR" ou "OPERADOR_PDV" deveria ter acesso ao cadastro rápido
- [ ] Diferenciar permissão de cadastro rápido (básico) vs cadastro completo (gerencial)
- [ ] Ajustar nível mínimo de permissão no backend para essa funcionalidade
- [ ] Testar cadastro com diferentes perfis de usuário
- [ ] Validar correção

---

## ❌ Login com e-mail inválido retorna "Erro interno do servidor" ao invés de mensagem amigável
**Data:** 06/02/2026
**Categoria:** 🔐 Autenticação / 💾 Sistema
**Prioridade:** Média
**Status:** 🔴 Pendente

**Descrição:**
Na tela de login do I9 Smart PDV, ao inserir um e-mail incorreto/inexistente e uma senha curta (menos de 6 caracteres), o sistema retorna a mensagem genérica "Erro interno do servidor" ao invés de uma mensagem clara como "E-mail ou senha inválidos". O erro interno está sendo exposto ao usuário final.

**Contexto observado (screenshot):**

- Tela: Login - "Bem-vindo - Faça login para acessar o sistema"
- E-mail ou CPF: operador4@m1autoposto.com.br
- Senha: ••• (menos de 6 caracteres)
- Erro exibido: "Erro interno do servidor" (fundo rosa/vermelho)
- Validação: "Senha deve ter pelo menos 6 caracteres" (texto em vermelho)
- Botões: "Voltar" e "Entrar"
- Rodapé: © 2025 I9 Smart PDV - Termos de Uso

**Impacto:**

- Mensagem confusa para o usuário — "Erro interno" sugere problema no sistema, não credencial errada
- Usuário pode pensar que o sistema está fora do ar
- Exposição de erro técnico ao usuário final (má prática de UX e segurança)
- Gera chamados de suporte desnecessários

**Ações necessárias:**

- [ ] Verificar tratamento de erro na rota de login no backend (catch genérico expondo erro interno)
- [ ] Retornar mensagem amigável "E-mail ou senha inválidos" para credenciais incorretas (status 401)
- [ ] Não expor detalhes de erro interno (status 500) ao usuário final
- [ ] Validar senha no frontend antes de enviar ao backend (mínimo 6 caracteres)
- [ ] Testar login com: e-mail inexistente, senha errada, senha curta, campos vazios
- [ ] Validar correção

---

## ❌ NFC-e rejeitada por NCM inexistente no item 2 (recorrente)
**Data:** 06/02/2026
**Categoria:** 🌐 Integração / 👤 Cadastro
**Prioridade:** Alta
**Status:** 🔴 Pendente

**Descrição:**
Ao finalizar vendas, a NFC-e é rejeitada pela SEFAZ com a mensagem "Informado NCM inexistente [nItem:2]". O item nº 2 das vendas possui um código NCM (Nomenclatura Comum do Mercosul) inválido ou desatualizado cadastrado no sistema, causando a rejeição do documento fiscal. Erro confirmado como **recorrente** em múltiplas vendas.

**Ocorrência 1 (screenshot):**

- Modal: "Gerenciador de Documento Fiscal"
- Venda #472 | NFC-e Nº 412 Série 502 | R$ 75,70 | FINALIZADA
- Status: REJEITADO
- Rejeição: "Informado NCM inexistente [nItem:2]"
- Referência: NFCE_b98fc2b2_a2a72f2f_1770420789196

**Ocorrência 2 (screenshot):**

- Modal: "Gerenciador de Documento Fiscal"
- Venda #478 | NFC-e Nº 413 Série 502 | R$ 126,15 | FINALIZADA | HOMOLOGAÇÃO
- Status: ERRO_AUTORIZACAO
- Rejeição: "Informado NCM inexistente [nItem:2]"
- Referência: NFCE_b98fc2b2_57fb4da0_1770674397753
- Ambiente: HOMOLOGAÇÃO (ambiente de testes)
- Opções: Atualizar Status, Retransmitir, Contingência

**Impacto:**

- Documento fiscal rejeitado, venda sem nota fiscal válida
- Produto com NCM incorreto impede emissão de qualquer nota que o contenha
- Pode afetar múltiplas vendas futuras com o mesmo produto
- Risco fiscal por acúmulo de notas rejeitadas

**Ações necessárias:**

- [ ] Identificar qual produto é o item nº 2 da venda #472
- [ ] Verificar o código NCM cadastrado para esse produto
- [ ] Consultar tabela NCM atualizada e corrigir o código no cadastro do produto
- [ ] Verificar se outros produtos possuem NCMs desatualizados ou inválidos
- [ ] Retransmitir a NFC-e após correção do NCM
- [ ] Considerar validação de NCM no momento do cadastro de produto para prevenir reincidência
- [ ] Validar correção

---

## ❌ Ações do carrinho travam após erro na venda (ESC, apagar produto, cancelar não funcionam)
**Data:** 06/02/2026
**Categoria:** 🐛 Bug / 🏢 Atendimento
**Prioridade:** Alta
**Status:** 🔴 Pendente

**Descrição:**
Após ocorrer um erro durante a finalização de uma venda (ex: erro de transmissão NFC-e, falha de conexão), ao fechar o modal de erro e retornar à tela do carrinho, as ações param de funcionar. O operador não consegue apagar produtos, cancelar a venda (ESC) nem realizar outras ações. A tela fica travada/bloqueada, forçando o operador a recarregar o sistema.

**Contexto observado (screenshot):**

- Modal: "Cancelar Venda?"
- Texto: "Tem certeza que deseja cancelar esta venda? Esta ação não pode ser desfeita e a venda cancelada NÃO poderá ser restaurada."
- Botões: "Voltar (ESC)" e "Cancelar Venda (Enter)"
- Problema: Mesmo com o modal visível, o ESC e Enter não respondem / ações anteriores no carrinho já estavam travadas

**Contexto adicional (screenshot - Atendimentos Pendentes):**

- Aba: "Nota Pendente" (1 pendência)
- Venda #478 | R$ 126,15 | 09/02, 18:59 | CONSUMIDOR FINAL
- Status: NFCE - REJEITADO
- Rejeição: "Informado NCM inexistente [nItem:2]"
- Botão: "Reemitir Nota Fiscal"
- A venda fica presa na lista de "Atendimentos Pendentes" e não sai, mesmo após tentativas de cancelamento

**Impacto:**

- Operador fica completamente travado após erro na venda
- Impossibilidade de cancelar, editar ou prosseguir com a venda
- Venda com erro permanece na lista de pendências sem possibilidade de remoção
- Pode ser necessário recarregar o sistema, perdendo dados em memória
- Acúmulo de vendas travadas na lista de pendentes polui a fila de atendimento
- Causa grande atraso no atendimento e frustração

**Ações necessárias:**

- [ ] Verificar se o modal de erro ao fechar está removendo event listeners ou bloqueando o estado da aplicação
- [ ] Garantir que o estado da venda volta ao normal após fechar modal de erro
- [ ] Verificar se há overlay/backdrop invisível bloqueando interações após fechar o modal de erro
- [ ] Restaurar handlers de teclado (ESC, Enter, atalhos) após fechar modais de erro
- [ ] Testar fluxo: finalizar venda → erro → fechar erro → tentar apagar produto / cancelar venda / usar atalhos
- [ ] Validar correção

---

## ❌ Abastecimento não chega nos bicos (integração CBC)
**Data:** 09/02/2026
**Categoria:** 🌐 Integração / 💾 Sistema
**Prioridade:** Alta
**Status:** 🔴 Pendente

**Descrição:**
Os abastecimentos realizados nas bombas não estão chegando nos bicos do sistema I9 PDV. A comunicação entre o Simulador/Manager CBC (Companytec Automação e Controle) e o sistema de vendas não está transmitindo os dados de abastecimento corretamente, impedindo que os bicos recebam as informações de volume e valor.

**Contexto observado (screenshot):**

- Simulador CBC Vr.2.2.0 - Companytec Automação e Controle
- Automação encontrada: CBC-06 Versão: 3.7 Serie: G-0 | Status: On Line
- 4 canais visíveis (Canal 1 a 4) com dados de abastecimento:
  - Canal 1: Total R$ 1.980 | Volume 338L | Preço R$ 5,890/L | Bicos 04/44 | **Bicos Bloqueados**
  - Canal 2: Total R$ 7.559 | Volume 675L | Preço R$ 11,23/L | Bicos 05/45 | **Bicos Bloqueados**
  - Canal 3: Total R$ 42.879 | Volume 728L | Preço R$ 5,890/L | Bicos 06/46 | **Bicos Bloqueados**
  - Canal 4: Total R$ 14.774 | Volume 1.313L | Preço R$ 11,23/L | Bicos 07/47 | **Bicos Bloqueados**
- Todos os bicos estão com status **"Bicos Bloqueados"**
- CBC Manager: Conexão RS-232 ativa, Ethernet LOCALHOST, Rede externa ativa
- Versão firmware: 3.7 | Versão monitor: 1.0 | Tensão bateria: 12,16V
- Status SENSOR e BICO com alertas (ícone de interrogação no BICO)

**Impacto:**

- Abastecimentos não são registrados no PDV
- Bicos ficam bloqueados impedindo vendas de combustível
- Operação do posto fica comprometida
- Possível perda de controle de estoque de combustível

**Ações necessárias:**

- [ ] Verificar comunicação entre CBC Manager e o sistema I9 PDV (API/WebSocket/polling)
- [ ] Verificar por que todos os bicos estão com status "Bloqueados"
- [ ] Analisar alerta no ícone BICO (interrogação) no CBC Manager
- [ ] Verificar configuração de rede (LOCALHOST / Ethernet / RS-232)
- [ ] Verificar se o serviço de integração CBC está rodando corretamente no servidor
- [ ] Testar desbloqueio manual dos bicos e verificar se abastecimento é registrado
- [ ] Validar correção

---

## ❌ Venda com erro de transmissão exibe status "Finalizada" ao invés de "Pendente"
**Data:** 10/02/2026
**Categoria:** 🐛 Bug / 💾 Sistema
**Prioridade:** Alta
**Status:** 🔴 Pendente

**Descrição:**
Ao consultar os detalhes de uma venda que apresentou erro na transmissão da NFC-e, o sistema exibe o status como "Finalizada" quando deveria estar como "Pendente". A venda não foi concluída com sucesso (documento fiscal rejeitado/não transmitido), mas o sistema marca como finalizada, gerando inconsistência entre o status real e o exibido.

**Contexto observado (screenshot):**

- Tela: "Detalhes da Venda #479"
- Status: **Finalizada** (tag verde)
- Data: 10/02/2026, 10:49
- Operador: Bruno Costa Almeida
- Cliente: CONSUMIDOR FINAL
- Item: Absorvente Noturno 8 Unidades - 1 x R$ 9,90
- Pagamento: Dinheiro R$ 9,90
- Subtotal: R$ 9,90 | Total: R$ 9,90
- Problema: A venda deu erro na transmissão mas aparece como "Finalizada"

**Impacto:**

- Status da venda não reflete a realidade (falso positivo)
- Operador/gerente não consegue identificar vendas com problemas fiscais
- Relatórios de vendas ficam incorretos (contam vendas com nota pendente como finalizadas)
- Dificulta o controle e auditoria fiscal
- Pode gerar divergências no fechamento de caixa

**Ações necessárias:**

- [ ] Verificar lógica de atualização de status da venda no backend
- [ ] Garantir que vendas com erro de transmissão NFC-e mantenham status "Pendente" ou "Erro Fiscal"
- [ ] O status só deve mudar para "Finalizada" após confirmação de autorização da NFC-e pela SEFAZ
- [ ] Verificar se o status é atualizado antes ou depois da transmissão fiscal
- [ ] Testar fluxo: venda → pagamento OK → transmissão falha → verificar status
- [ ] Validar correção

---

**Última atualização:** 10/02/2026
