# Frameworks Ágeis
### Scrum
 Usados para orientar as atividades de desenvolvimento dentro deum processo que incorpora as seguintes atividades metodológicas: requisitos, análise, projeto, evolução e entrega. Em cada atividade metodológica, ocorrem tarefas realizadas em um período chamado de sprint. O trabalho realizado dentro de um sprint (o número de sprints necessários para cada atividade metodológica varia dependendo do tamanho e da complexidade do produto) é adaptado ao problema em questão e definido, e muitas vezes modicado em tempo real, pela equipe Scrum.
 
![[ag-scrum.png]]
#### Estrutura
É composta por um product owner, um Scrum master (ajudador, facilitador, orientador) e uma pequena equipe de desenvolvimento (três a seis pessoas), no qual não há nenhuma hierarquia definida. Os principais artefatos do Scrum são o backlog do produto, o backlog do sprint e o incremento de código. O desenvolvimento avança pela
divisão do projeto em uma série de períodos de desenvolvimento incremental do protótipo, com duração de 2 a 4 semanas, chamados de sprints. 
#### Reunião Diária
Evento de 15 minutos programado no início de cada dia de trabalho para permitir que os membros da equipe sincronizem as suas atividades e se planejem para as próximas 24 horas. O Scrum master e a equipe de desenvolvimento sempre participam da reunião diária. São feitas três perguntas-chave que são respondidas por todos os membros da equipe:
- O que você realizou desde a última reunião de equipe?
- Quais obstáculos está encontrando?
- O que planeja realizar até a próxima reunião da equipe?
### XP (eXtreme Programming)
A Extreme Programming (Programação Extrema) envolve um conjunto de regras e práticas constantes no contexto de quatro atividades metodológicas: planejamento, projeto, codificação e testes.

![[ag-xp.png]]
#### Planejamento
Se inicia com ouvir. A atividade de ouvir conduz à criação de um conjunto de histórias do usuário. Cada história de usuário é escrita pelo cliente e colocada em uma ficha. O cliente atribui um valor à história baseando-se no valor de negócio global do recurso ou da função. Os membros da equipe XP avaliam, então, cada história e atribuem um custo, medido em semanas de desenvolvimento. A equipe XP ordena as histórias que serão desenvolvidas em uma de três formas: (1) todas as histórias serão implementadas imediatamente (em um prazo de poucas semanas); (2) as histórias de maior valor serão deslocadas para cima no cronograma e implementadas primeiro; ou (3) as histórias de maior risco serão deslocadas para cima no cronograma e implementadas primeiro.
#### Projeto
O projeto XP segue rigorosamente o princípio KISS (keep it simple, stupid!). Os cartões CRC (mecanismo eficaz para
pensar o software em um contexto orientado a objetos) são o único artefato de projeto produzido como parte do processo XP. Refatoração (modicar/otimizar o código sem alterar o comportamento externo do software) significa que o “projetar” é realizado continuamente enquanto o sistema estiver em elaboração.
#### Codificação
A primeira etapa é a implementação da metodologia TDD para desenvolver os testes de unidade que exercitarão cada uma das histórias a ser incluída na versão corrente. Um conceito-chave na atividade de codificação (e um dos mais discutidos aspectos da XP) é a programação em pares.
#### Testes
Os testes de unidades criados devem ser implementados usando-se uma metodologia que os capacite a ser automatizados. Isso estimula uma estratégia de testes de regressão. Os testes de aceitação da XP, também denominados testes de cliente, são especificados pelo cliente e mantêm o foco nas características e na funcionalidade do sistema total que são visíveis e que podem ser revistas pelo cliente. Os testes de aceitação são obtidos de histórias de usuário implementadas como parte de uma versão do software.
### Kanban
Abordagem para gerenciar alterações e entregar serviços. Ele define o processo para integrar alterações solicitadas em sistemas baseados em software e incentiva a entrega de serviços com foco nas necessidades do cliente. Os membros da equipe têm liberdade para organizar seu trabalho e as políticas evoluem para melhorar os resultados.

- As reuniões de equipe para o Kanban são semelhantes àquelas realizadas na metodologia Scrum. 
- A base para a reunião diária em pé do Kanban (standup meeting) é uma tarefa conhecida como “caminhar pelo quadro”. 

O Kanban depende de seis práticas fundamentais:

1. Visualizar o fluxo de trabalho: Usando um quadro Kanban, as etapas de desenvolvimento são representadas por colunas, onde os cartões movem-se de "por fazer" para "fazendo" e "feito" conforme o progresso do projeto.
2. Limitar o trabalho em progresso (WIP): Ao limitar a quantidade de trabalho em andamento, os desenvolvedores são incentivados a completar suas tarefas antes de iniciar novas, reduzindo o tempo de ciclo e melhorando a qualidade do trabalho.
3. Gerenciar o fluxo de trabalho: Isso envolve entender o fluxo de valor — Trajeto que um item de trabalho percorre desde sua concepção até sua entrega final ao cliente. Ele engloba todas as etapas e atividades necessárias para transformar uma ideia ou requisito em um produto ou serviço pronto para uso —, identificar interrupções, definir e implementar mudanças para reduzir desperdícios.
4. Explicitar políticas de processo: Registrar os critérios para selecionar e concluir itens de trabalho.
5. Enfatizar a melhoria contínua: Criar ciclos de feedback baseados em dados de processo e medir os efeitos das mudanças implementadas.
6. Mudar o processo colaborativamente: Engajar todos os membros da equipe e partes interessadas na alteração do processo, conforme necessário.

![[ag-kanban.png]]
# DevOps
O DevOps tenta aplicar os princípios do desenvolvimento ágil e do enxuto a toda a cadeia logística de software.

![[ag-devops.png]]

#### Desenvolvimento contínuo
Os produtos de software são divididos e desenvolvidos em múltiplos sprints, com os incrementos entregues para os membros da garantia da qualidade da equipe de desenvolvimento para serem testados.
#### Teste contínuo
Ferramentas de teste automatizadas são utilizadas para ajudar os membros da equipe a testar múltiplos incrementos de código ao mesmo tempo para garantir que não há defeitos antes da integração.
#### Integração contínua
Os elementos de código com a nova funcionalidade são adicionados ao código existente e ao ambiente de execução (runtime) e, então, examinados para garantir que não há erros após a entrega.
#### Entrega contínua
Nesta etapa, o código integrado é entregue (instalado) ao ambiente de produção, que pode incluir múltiplos locais em nível global, que, por sua vez, precisam ser preparados para receber a nova funcionalidade. 
#### Monitoramento contínuo
Os membros da equipe de operações que pertencem à equipe de desenvolvimento ajudam a melhorar a qualidade do software, monitorando o seu desempenho no ambiente de produção e buscando proativamente possíveis problemas antes que os usuários os identifiquem.
# História do Usuário
É uma descrição simples e genérica de uma funcionalidade de software a partir da experiência do usuário. Ela define o que um usuário precisa da sua empresa, o que ajuda a priorizar o trabalho e a aumentar o valor para o cliente.

Normalmente, uma história de usuário segue o seguinte formato:
_"Como [tipo de usuário], eu quero [meta ou objetivo] para que eu [benefício ou resultado]."_
# Backlog do Produto
Backlog do produto é uma lista que contém os requisitos necessários para a construção de um produto de alto valor. Ou seja, trata-se de uma lista de entregas do projeto organizada pelo Product Owner em ordem de prioridade. O backlog de produto serve para definir o ciclo de vida de um produto. Ele mostra suas fases, o que precisa ser feito para alcançar determinado resultado e como e para quando fazer.

No topo estão os itens mais importantes e desenvolvidos. Já para o final, constam os elementos que estão em fase de desenvolvimento e ainda não foram completamente estruturados.

![[ag-backlog.png]]
#### Estrutura de um Backlog
1. Levantamento de Requisitos.
2. Critérios de Priorização.
	1. Moscow -  Permite que todos os stakeholders e membros do time acordem em uma ordem de importância. Assim, as expectativas são ajustadas ao que será entregue como Mínimo Produto Viável (MVP). Sendo dividido em tarefas classificadas como _Must have_, _Should have_, _Could have_, _Wouldn't Have_.
	2. Scorecard - Cada critério terá seu peso, recebendo uma nota de 0 a 100. Finalmente, utilizando a média ponderada para calcular a priorização.
	3. BUC - Prioridade de acordo com o custo ou receita gerada.
	4. Teste e Suposição - Define a prioridade a partir dos resultados da validação de uma hipótese ou suposição, e também da relevância para o usuário final.  _T = O quanto a suposição foi testada_, _U = Relevância para o usuário_. A prioridade é o resultado da soma destes dois critérios.
	5. Valor de Negócio x Risco - Um dos métodos mais comuns de priorização é analisar o valor de negócio e o risco de cada item.
3. Nomeação de itens. (Testes da funcionalidades X, Implementação da funcionalidade Y, Distribuir Pesquisa)
4. Descrição dos itens criados.
5. Definição de prazo para cada item.