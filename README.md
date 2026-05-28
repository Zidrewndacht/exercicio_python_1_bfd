# Atividades de Python – Especificações para Duplas

**Público-alvo:** Estudantes de nível médio com ~12h de aulas prévias de Python.  
**Tempo:** ~2 horas por dupla.  
**Restrições:** Não usar bibliotecas externas, `try/except`, classes, `assert`, dicionários, tuplas, manipulação de arquivos, múltiplos módulos/arquivos.  
**Recursos permitidos:** Documentação online, busca na Web, chatbots de IA (não agentes autônomos).  

**Requisitos mínimos por atividade:**
- Menu inicial com `while` para repetição até o usuário escolher sair.
- Pelo menos uma funcionalidade que exija loop `for` (`range()` ou iterando em lista).
- Funções reutilizáveis em pelo menos dois pontos distintos do programa.
- Uso de condicionais (`if/elif/else`), operadores aritméticos, lógicos e de comparação.
- Uso de listas: criação, acesso, métodos e/ou comprehensions.
- Entrada/saída com `input()`/`print()` e f-strings.
- Código em um único arquivo, com capacidade de atingir ~200 linhas.

---

## Tarefa 1: Orçamento Pessoal Semanal

**Contexto:** Uma pessoa deseja controlar suas despesas semanais para não ultrapassar um limite definido. O programa deve permitir o registro diário de gastos, análise por categoria e alertas quando o total se aproxima do limite.

**Menu inicial (loop infinito até sair):**
1. Definir orçamento semanal e limite de alerta (em %).
2. Registrar nova despesa (dia da semana, categoria, valor).
3. Listar todas as despesas registradas (formato tabular simples com f-strings).
4. Resumo por categoria (mostrar categoria, total gasto e % do orçamento total).
5. Verificar situação do orçamento (total gasto, restante, se ultrapassou ou está abaixo do limite de alerta).
6. Estatísticas dos dias (qual dia teve maior gasto, qual teve menor, média diária).
7. Resetar todos os dados (limpar listas após confirmação).
0. Sair.

**Comportamento esperado:**
- Ao iniciar, se não houver orçamento definido, as opções 2-6 devem avisar que é necessário definir o orçamento primeiro.
- O limite de alerta é um percentual (ex: 80%). Se o total gasto atingir ou ultrapassar esse percentual do orçamento, a opção 5 deve exibir um aviso.
- Categorias são strings livres digitadas pelo usuário (ex: "Alimentação", "Transporte").
- Dias da semana devem ser validados: apenas "segunda", "terça", "quarta", "quinta", "sexta", "sábado", "domingo" (aceitar com ou sem acento, mas armazenar padronizado).
- A opção 4 deve iterar sobre as despesas, acumular por categoria e exibir uma linha por categoria encontrada.
- A opção 6 deve calcular o total por dia (usando loop), identificar o maior e o menor, e a média de gasto por dia (considere apenas dias que tiveram gastos, não todos os 7).
- A opção 7 deve pedir confirmação ("S" ou "N") antes de limpar.

**Tarefas bônus:**
- B1. Permitir que o usuário "corrija" uma despesa: escolher um índice da lista e alterar seu valor (sem usar dicionários).
- B2. Mostrar um "gráfico" textual de barras para o resumo por categoria (ex: "Alimentação: ████████" onde cada bloco representa R$10).

---

## Tarefa 2: Gerenciador de Tarefas de Projeto

**Contexto:** Uma equipe pequena precisa acompanhar tarefas de um projeto simples. Cada tarefa tem descrição, responsável, prioridade (Alta, Média, Baixa) e status (Pendente, Em andamento, Concluída).

**Menu inicial:**
1. Adicionar nova tarefa (descrição, responsável, prioridade).
2. Listar todas as tarefas (mostrar índice, descrição, responsável, prioridade, status).
3. Alterar status de uma tarefa (informar índice; ciclar entre Pendente → Em andamento → Concluída).
4. Filtrar por responsável (mostrar apenas tarefas de uma pessoa digitada).
5. Filtrar por prioridade (mostrar apenas Alta, ou apenas Média, ou apenas Baixa).
6. Relatório de produtividade (total de tarefas, quantas concluídas, % de conclusão, quantas por prioridade).
7. Remover tarefas concluídas (perguntar se deseja remover todas de uma vez ou informar índice; pedir confirmação).
0. Sair.

**Comportamento esperado:**
- Prioridade só aceita "Alta", "Média" ou "Baixa" (validar entrada, não diferenciar maiúsculas/minúsculas, mas armazenar com primeira letra maiúscula).
- Status inicial sempre "Pendente".
- A opção 3 deve validar se o índice existe; se a tarefa já estiver "Concluída", ao "avançar" status volta para "Pendente" (ciclo).
- A opção 4 deve fazer busca case-insensitive no nome do responsável.
- A opção 6 deve calcular percentuais com 1 casa decimal. Se não houver tarefas, mostrar mensagem apropriada.
- A opção 7, se escolhida remoção em massa, deve percorrer a lista de trás para frente (ou construir nova lista) para evitar problemas de índice.
- O programa deve ter uma função de formatação de exibição de tarefa reutilizada nas opções 2, 4 e 5.

**Tarefas bônus:**
- B1. Implementar ordenação manual: permitir que o usuário reordene a lista trocando duas tarefas de posição (informar dois índices).
- B2. Implementar busca parcial: encontrar tarefas onde a descrição contenha uma palavra digitada.

---

## Tarefa 3: Conversor e Calculadora de Saúde/Fitness

**Contexto:** Um aplicativo simples para auxiliar em cálculos de saúde e conversões físicas usadas no dia a dia.

**Menu inicial:**
1. Calculadora de IMC (peso e altura; mostrar valor e classificação: Abaixo do peso, Normal, Sobrepeso, Obesidade).
2. Conversor de temperaturas (Celsius ↔ Fahrenheit ↔ Kelvin; escolher origem e destino).
3. Conversor de distâncias (km ↔ milhas ↔ metros; escolher origem, destino e valor).
4. Calculadora de ritmo de corrida (distância em km, tempo em minutos; mostrar pace min/km e velocidade km/h).
5. Calculadora de gasto calórico estimado (atividade: caminhada, corrida, ciclismo; peso em kg; duração em min; usar METs aproximados: 3.5, 9.8, 7.5 respectivamente; fórmula: calorias = MET × peso × (min/60)).
6. Registro de medições corporais (data, peso, cintura, quadril; armazenar e listar histórico).
7. Análise do histórico de medições (mostrar evolução do peso: primeira, última, menor, maior, média; calcular razão cintura/quadril média).
0. Sair.

**Comportamento esperado:**
- Todas as entradas numéricas devem ser validadas: não aceitar valores negativos ou zero onde não faça sentido (ex: peso, distância).
- O IMC deve ser calculado com a fórmula padrão e a classificação deve usar condicionais encadeadas.
- O conversor de temperaturas deve ter uma função de conversão reutilizável (ou múltiplas funções) que seja chamada independentemente da direção escolhida.
- O histórico (opção 6) deve armazenar entradas em listas paralelas ou estrutura que permita acesso posterior.
- A opção 7 deve iterar sobre o histórico e calcular as estatísticas solicitadas. Se o histórico estiver vazio, avisar.
- A formatação de saída deve usar f-strings com alinhamento para facilitar leitura.

**Tarefas bônus:**
- B1. Adicionar uma opção para calcular quantos litros de água recomendados por dia com base no peso (fórmula: 35 ml por kg, mostrar em litros).
- B2. Criar uma opção que simule um plano de caminhada: usuário informa dias disponíveis na semana (1-7) e meta semanal em km; o programa sugere km por dia (distribuição igual, com resto no último dia).

---

## Tarefa 4: Sistema de Apuração de Enquete/Votação

**Contexto:** Uma escola precisa de um sistema simples para apurar votação para representante de turma. Vários candidatos podem ser registrados e os votos são computados manualmente (simulando uma urna eletrônica simplificada).

**Menu inicial:**
1. Cadastrar candidatos (nome; não permitir nomes duplicados, ignorando maiúsculas/minúsculas).
2. Registrar voto (escolher candidato pelo número de índice ou nome; validar existência).
3. Registrar voto em branco (contabilizar separadamente).
4. Apurar resultados (mostrar cada candidato, total de votos, % sobre o total válido; mostrar votos em branco e % sobre o total geral).
5. Estatísticas da votação (total de votos, candidato mais votado, candidato menos votado, se houve empate no primeiro lugar).
6. Simular múltiplos votos (permitir digitar uma sequência de votos separados por vírgula, ex: "1,2,1,3,0" onde 0 = branco; validar cada um e registrar).
7. Resetar votação (zerar todos os votos, mantendo candidatos cadastrados; pedir confirmação).
0. Sair.

**Comportamento esperado:**
- Candidatos são armazenados em uma lista. Votos podem ser armazenados em lista paralela de inteiros (índice 0 = candidato 0, etc.) ou outra estrutura equivalente usando apenas listas.
- Votos em branco devem ser armazenados em variável separada.
- A opção 4 deve calcular o total válido (excluindo brancos) e o total geral. Percentuais com 2 casas decimais.
- A opção 5 deve determinar o mais votado e o menos votado usando loops e comparações. Se houver empate no primeiro lugar, informar todos os empatados.
- A opção 6 deve receber uma string, separar os elementos (usando `.split(',')`), converter para inteiros, e iterar registrando cada voto. Votos inválidos (número de candidato inexistente, não inteiro, etc.) devem ser contados como "nulos" e ignorados com mensagem de aviso, mas sem interromper o processamento dos demais.
- Não deve ser possível votar se não houver candidatos cadastrados.

**Tarefas bônus:**
- B1. Adicionar opção de "segundo turno": verificar se o mais votado tem mais de 50% dos votos válidos. Se sim, declarar vencedor. Se não, listar os dois mais votados como candidatos ao segundo turno.
- B2. Histórico de votação: registrar a ordem dos votos (log) em uma lista e permitir exibi-la (ex: "Voto 1: Maria", "Voto 2: Branco", etc.).

---

## Tarefa 5: Controle de Estoque de Pequena Loja

**Contexto:** Uma pequena loja precisa controlar produtos, quantidades e valores. O sistema deve permitir entrada e saída de mercadorias e alertar sobre itens em baixa quantidade.

**Menu inicial:**
1. Cadastrar produto (nome, quantidade inicial, preço unitário, quantidade mínima para alerta).
2. Registrar entrada de estoque (informar produto pelo índice ou nome; informar quantidade a adicionar; validar se quantidade é positiva).
3. Registrar saída/venda (informar produto e quantidade vendida; validar se há quantidade suficiente; se a quantidade resultante ficar abaixo do mínimo, exibir alerta).
4. Listar todos os produtos (mostrar índice, nome, quantidade atual, preço, valor total em estoque, status: "OK" ou "BAIXO" se abaixo do mínimo).
5. Relatório de valorização (calcular o valor total do estoque da loja; listar produtos ordenados por valor total em estoque – do maior para o menor; usar ordenação manual com loops, não usar `.sort()` com chave).
6. Produtos em alerta (listar apenas aqueles cuja quantidade atual ≤ quantidade mínima).
7. Editar produto (permitir alterar nome, preço ou quantidade mínima de um produto existente; não permitir alterar quantidade atual por aqui, apenas via entrada/saída).
0. Sair.

**Comportamento esperado:**
- Cada produto deve ter seus dados armazenados de forma que seja possível acessar nome, quantidade, preço e mínimo. Como não há dicionários, use listas paralelas ou uma única lista onde cada elemento é uma string formatada com separador (ex: "nome|qtde|preco|min") – a escolha da estrutura é do estudante, desde que funcione.
- A opção 3 deve verificar se a quantidade em estoque é suficiente. Se não for, recusar a operação. Se for, subtrair e verificar se ficou abaixo do mínimo.
- A opção 5 deve calcular valor total em estoque (quantidade × preço) para cada produto, e ordenar manualmente (ex: usando bubble sort ou seleção) com base no valor total. Mostrar a lista ordenada.
- A opção 6 deve usar loop para verificar condição e exibir apenas os que atendem.
- Deve haver uma função reutilizável para localizar um produto pelo nome (case-insensitive) ou pelo índice, usada nas opções 2, 3, 6 e 7.

**Tarefas bônus:**
- B1. Implementar uma opção de "reposição automática": para cada produto em alerta, sugerir uma quantidade a comprar para atingir o dobro da quantidade mínima, e calcular o investimento necessário.
- B2. Criar um simulador de promoção: usuário informa % de desconto; o programa recalcula o preço de todos os produtos e mostra o impacto no valor total do estoque (antes e depois).

---

## Tarefa 6: Agenda de Contatos e Aniversários

**Contexto:** Uma agenda simples para manter contatos pessoais com data de aniversário, telefone e e-mail. Deve permitir buscas e lembretes de aniversariantes do mês.

**Menu inicial:**
1. Adicionar contato (nome, telefone, e-mail, dia do aniversário, mês do aniversário).
2. Listar todos os contatos (ordem alfabética; ordenar manualmente com loops, não usar `.sort()`).
3. Buscar contato (por nome parcial ou por telefone exato; mostrar todos que correspondem).
4. Remover contato (buscar por nome; se houver múltiplos com mesmo nome, mostrar índices e pedir confirmação de qual remover).
5. Aniversariantes do mês (usuário informa número do mês; mostrar todos os contatos que fazem aniversário naquele mês, ordenados pelo dia do aniversário – ordenação manual).
6. Estatísticas dos contatos (total de contatos, quantos têm e-mail preenchido vs. vazio, média do dia de aniversário – considerar apenas o dia, não o mês).
7. Atualizar contato (buscar por nome/telefone; permitir alterar qualquer campo individualmente).
0. Sair.

**Comportamento esperado:**
- Dia e mês devem ser validados: dia entre 1 e 31, mês entre 1 e 12. Não é necessário validar dias específicos de cada mês (ex: 31/02 pode ser aceito, mas idealmente avisar que é inválido se o estudante quiser implementar).
- A ordenação alfabética (opção 2) deve ser implementada manualmente (ex: bubble sort comparando strings). O Python compara strings lexicograficamente com operadores `<`, `>`, então isso é possível com loops.
- A busca (opção 3) por nome parcial deve verificar se a substring digitada está contida no nome (case-insensitive). A busca por telefone deve ser exata.
- A opção 5 deve filtrar por mês e ordenar manualmente pelo dia do aniversário (ordem crescente).
- A opção 7 deve mostrar os dados atuais e perguntar qual campo deseja alterar (1-Nome, 2-Telefone, etc.), aplicando apenas o escolhido.
- Deve existir uma função de exibição de contato formatada reutilizada em pelo menos 3 opções diferentes.

**Tarefas bônus:**
- B1. Criar uma opção "Próximos aniversariantes": simular que hoje é uma data informada pelo usuário (dia e mês); mostrar contatos cujo aniversário ocorra nos próximos 30 dias (simplificado: considerar apenas o mês atual e o seguinte, sem calcular precisamente 30 dias).
- B2. Exportar visualmente: gerar uma string formatada que simule um "cartão de visita" para um contato selecionado, usando caracteres ASCII (bordas com `+`, `-`, `|`).

---

## Tarefa 7: Diário de Classe e Boletim Escolar

**Contexto:** Professor precisa registrar notas de uma turma, calcular médias, situação final e estatísticas gerais.

**Menu inicial:**
1. Cadastrar aluno (nome; não permitir nomes duplicados, case-insensitive).
2. Registrar notas de um aluno (buscar por nome; registrar 3 notas bimestrais; validar se cada nota está entre 0 e 10).
3. Listar alunos e médias (mostrar nome, as 3 notas, média aritmética, situação: Aprovado se média ≥ 7, Recuperação se 5 ≤ média < 7, Reprovado se média < 5).
4. Estatísticas da turma (média geral da turma, maior média, menor média, quantidade de aprovados, recuperação, reprovados, % de aprovação).
5. Alunos em recuperação (listar apenas alunos com média entre 5.0 e 6.9).
6. Simular nota de recuperação (escolher aluno em recuperação; informar nota da recuperação; calcular nova média como: (média anterior + nota recuperação) / 2; mostrar nova situação).
7. Ranking da turma (ordenar alunos por média final, do maior para o menor; ordenação manual; mostrar posição, nome e média).
0. Sair.

**Comportamento esperado:**
- Notas devem ser validadas: apenas números entre 0.0 e 10.0.
- A média deve ser calculada com precisão de 1 casa decimal.
- A estrutura de dados deve permitir associar um aluno a suas 3 notas. Como não há dicionários, o estudante deve usar listas paralelas ou outra estrutura baseada em listas/strings.
- A opção 4 deve iterar sobre todos os alunos com notas completas. Se um aluno tiver menos de 3 notas, deve ser ignorado nas estatísticas com um aviso, mas não travar o cálculo.
- A opção 6 só deve funcionar para alunos que estejam em recuperação (média entre 5 e 6.9). Após calcular, atualizar a média do aluno e sua situação.
- A ordenação do ranking (opção 7) deve ser manual (ex: selection sort ou bubble sort) com base na média.
- Uma função de cálculo de média deve ser reutilizada nas opções 3, 4, 5, 6 e 7.

**Tarefas bônus:**
- B1. Implementar um sistema de frequência: adicionar registro de faltas para cada aluno. Se faltas > 25% das aulas (considerar 20 aulas no total), o aluno fica "Reprovado por Falta" independentemente da média.
- B2. Curva de notas: permitir ao professor aplicar um bônus de até 1 ponto para todos os alunos, respeitando o teto de 10. Mostrar antes e depois.

---

## Tarefa 8: Caixa Eletrônico e Gerenciador de Contas Simples

**Contexto:** Simular um caixa eletrônico para uma ou mais contas bancárias simples (sem persistência em arquivo). O sistema deve permitir depósitos, saques, transferências entre contas cadastradas no próprio programa, e extrato.

**Menu inicial:**
1. Criar conta (nome do titular, saldo inicial ≥ 0; gerar número de conta sequencial automático iniciando em 1001).
2. Listar contas (número, titular, saldo formatado em moeda).
3. Depositar (informar número da conta; validar existência; informar valor; apenas positivos).
4. Sacar (informar número da conta; validar existência e saldo suficiente; valor positivo).
5. Transferir (informar conta origem e conta destino; validar ambas, saldo suficiente na origem; executar débito na origem e crédito no destino; registrar no extrato de ambas).
6. Extrato da conta (informar número da conta; mostrar titular, saldo atual, e histórico de movimentações: depósitos, saques, transferências enviadas/recebidas com valores e sinais).
7. Simular rendimento (aplicar um percentual de rendimento a todas as contas; mostrar saldo anterior e novo saldo de cada uma).
0. Sair.

**Comportamento esperado:**
- Cada conta deve ter: número, titular, saldo, e histórico de movimentações. Como não há dicionários ou classes, o estudante deve usar listas paralelas ou uma lista de strings formatadas. O histórico pode ser uma lista de strings associada à conta (ex: lista de listas, ou lista paralela de listas).
- O número da conta deve ser gerado automaticamente: a primeira conta é 1001, a segunda 1002, etc. (usar uma variável contadora ou calcular com base no tamanho da lista + 1001).
- Todas as operações financeiras devem validar valores positivos (exceto rendimento, que é percentual positivo).
- A opção 5 (transferência) deve ser atômica: se a origem não tiver saldo, cancelar totalmente. Se funcionar, deve adicionar uma movimentação no extrato da origem ("Transferência enviada -X para conta Y") e no destino ("Transferência recebida +X da conta Y").
- O extrato (opção 6) deve mostrar as movimentações na ordem em que ocorreram. Se não houver movimentações, informar "Sem movimentações".
- A opção 7 deve solicitar um percentual (ex: 0.5 para 0,5%) e aplicar a todas as contas: novo_saldo = saldo * (1 + percentual/100). Mostrar em formato tabular.
- Deve haver uma função de busca de conta por número reutilizada em pelo menos 4 opções.

**Tarefas bônus:**
- B1. Implementar uma opção de "poupança meta": o usuário informa uma conta e um valor meta; o programa calcula quantos meses serão necessários para atingir a meta, considerando um rendimento mensal fixo informado (juros simples: saldo + (saldo * taxa/100 * meses) ≥ meta).
- B2. Criar uma opção de "dividir conta": informar valor total, número de contas destino, e distribuir igualmente (com tratamento de centavos: o último recebe o resto se houver divisão não exata).

---

## Instruções Gerais para os Alunos

1. **Leiam toda a especificação antes de começar.** Entendam o que cada opção do menu deve fazer.
2. **Planejem juntos.** Discutam quais listas/variáveis serão necessárias e como organizar os dados antes de codificar.
3. **Testem incrementalmente.** Implementem uma opção do menu, testem-na bem, e só depois passem para a próxima.
4. **Usem funções.** Identifiquem trechos de código repetidos e transformem-nos em funções reutilizáveis.
5. **Validem entradas.** O programa não deve quebrar se o usuário digitar texto onde se espera número, ou um índice que não existe. (Nota: sem `try/except`, usem condicionais e métodos de string para validar quando possível.)
6. **Formatação importa.** Usem f-strings para deixar a saída legível e organizada.
7. **Se terminarem cedo**, tentem implementar as tarefas bônus. Elas são desafiadoras e podem exigir raciocínio extra.

**Critérios de avaliação sugeridos:**
- Funcionalidade: o programa faz o que foi pedido?
- Organização: uso adequado de funções e repetição de código mínima.
- Validação: o programa lida bem com entradas inesperadas?
- Clareza: nomes de variáveis e funções são significativos?
- Colaboração: ambos os membros da dupla participaram?

Bom trabalho!
