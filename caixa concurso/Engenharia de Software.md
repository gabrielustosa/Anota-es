# Processo Unificado 
Um conjunto de atividades executadas para transformar um conjunto de requisitos do cliente em um sistema de software.

- É baseado em componentes que utilizam interfaces.
- Utiliza toda uma definição em UML.
- Dirigido por casos de usos
- Centrado na arquitetura, Interativo e incremental

É geralmente descrito sobre três perspectivas:

1. Uma perspectiva dinâmica, que mostra as fases do modelo ao longo do tempo.
2. Uma perspectiva estática, que mostra as atividades realizadas no processo.
3. Uma perspectiva prática, que sugere boas práticas a serem usadas durante o processo.

 ```ad-info
 ##### Arquitetura
É um "mapa" do sistema, definindo partes do mesmo como relacionamentos, iterações, mecanismos. implementação, distribuição. É fundamental para entender a visão global, as possibilidades de reuso e evolução do sistema. 
##### Iterativo e incremental
O software não é implementado a partir de um instante no fim do projeto, o ciclo de vida no PU é implementado em iterações.
##### Iterações
É um miniprojeto que resulta em uma versão do sistema liberada interna ou externamente. Essa versão oferece uma melhora incremental sobre a interação anterior. 
```
#### Ciclo de Vida
É decomposto ao longo do tempo em quatro fases sequenciais, cada uma concluída por um marco importante; cada fase é essencialmente um período de tempo entre dois marcos principais. Ao final de cada fase, é realizada uma avaliação para determinar se os objetivos da fase foram cumpridos. Uma avaliação satisfatória permite que o projeto passe para a próxima fase. As 4 quatro fases sequenciais são: **Concepção (Inception), Elaboração (Elaboration),  Construção (Construction) e Transição (Transition)**. Cada fase, é subdivida em iterações que passam por todos os cinco fluxos do trabalho do processo: **Requisitos, Análise, Implementação e Testes**.

- Não se comporta como modelo de cascata, são estreitamente relacionadas ao negócio, e não a assuntos técnicos. 
- Os fluxos de trabalho podem ser realizados a qualquer momento durante o ciclo de desenvolvimento.
- Disciplinas podem ter mais ênfase do que outras.

![[engs-pu-ciclo.png]]

 ##### Concepção
  Estabelecer um business case para o sistema. Você deve identificar todas as entidades externas (pessoas e sistemas) que vão interagir com o sistema e definir as interações. Então, você deve usar essas informações para avaliar a contribuição do sistema para o negócio. Se essa contribuição for pequena, então o projeto poderá ser cancelado depois dessa fase.
 ##### Elaboração
 Desenvolver uma compreensão do problema dominante, estabelecer um framework da arquitetura para o sistema, desenvolver o plano do projeto e identificar os maiores riscos do projeto. No fim dessa fase, você deve ter um modelo de requisitos para o sistema, que pode ser um conjunto de casos de uso da UML, uma descrição da arquitetura ou um plano de desenvolvimento do software.
 ##### Construção
 A fase de construção envolve projeto, programação e testes do sistema. Durante essa fase, as partes do sistema são desenvolvidas em paralelo e integradas. Na conclusão dessa fase, você deve ter um sistema de software já funcionando, bem como a documentação associada pronta para ser entregue aos usuários.
 ##### Transição
 Implica transferência do sistema da comunidade de desenvolvimento para a comunidade de usuários e em seu funcionamento em um ambiente real. Isso é ignorado na maioria dos modelos de processo de software, mas é, de fato, uma atividade cara e, às vezes, problemática. Na conclusão dessa fase, você deve ter um sistema de software documentado e funcionando corretamente em seu ambiente operacional.
#### 4 Ps (Pessoa, Projeto, Produto e Processo)
 ##### Pessoas
 Financiam, escolhem, desenvolvem, gerenciam, testam, usam e são beneficiadas pelo produto.
 ##### Projetos
 Sofrem alterações, determinam os tipos de pessoas que irão trabalhar no projeto e os **artefatos** que serão usados.
 ##### Produto
 Código fonte, diagramas e outros artefatos
 ##### Processo
 Define **quem (papel/pessoa/trabalhadores)** faz **o que (artefato)**, **quando (disciplina)** e **como (atividades)**

```ad-info
##### Artefato
É qualquer tipo de informação criada por uma pessoa (diagramas UML, textos, modelos, interfaces)
##### Trabalhadores
Responsável pela produção ou modificação de artefatos; Exemplos (programador, analista, testador)
##### Atividades
Tarefa que o trabalhador executa afim de produzir ou modificar um artefato.
##### Disciplina
Descreve as sequências das atividades e as iterações com que participa, sendo realizadas a qualquer momento do ciclo.

```
#### Casos de usos
Um caso de uso é uma sequência de ações, executada por atores que produzem um ou mais resultados de valor para outros atores.

- Possibilitam que os requisitos funcionais possam ser capturados na perspectiva de cada usuário do sistema.
- Os testes são baseados nos casos de usos.
- Os requisitos funcionais são expressões através dos casos de uso, que são adicionados a cada interação.

```ad-info
###### Atores
É uma pessoa ou outro sistema
```
# UML
#TODO
#### Diagramas de classe
Foca na estrutura interna do sistema, representando classes, seus atributos, métodos e as relações entre elas.

- **Modelagem da Estrutura:** Utilizado para modelar a estrutura estática do sistema, incluindo as entidades do domínio, suas propriedades e os relacionamentos entre elas.
- **Não envolve atores diretamente:** Não representa atores (usuários ou sistemas externos) interagindo com o sistema.
#### Diagramas de casos de uso
O Diagrama de Casos de Uso foca no comportamento do sistema do ponto de vista dos usuários, representando as interações entre atores e casos de uso.

- **Modelagem do Comportamento:** Utilizado para modelar o comportamento do sistema, mostrando como os usuários interagem com o sistema por meio de casos de uso.
- **Envolvimento Direto de Atores:** Atores (usuários ou sistemas externos) são parte fundamental do diagrama, representando quem interage com o sistema.
# Métricas 
Métrica é a medição de uma propriedade de uma determinada entidade (produto, processo ou recursos).
# Engenharia de Requisitos
Os requisitos de um sistema são as descrições do que o sistema deve fazer, os serviços que oferece e as restrições a seu funcionamento. Este, é o processo de descobrir, analisar, documentar e verificar esses serviços e restrições. Idealmente, eles devem especificar somente o comportamento externo do sistema. A elaboração de requisitos é norteada pela criação e pelo refinamento de cenários que descrevem como o usuário e outros atores interagirão com o sistema. Cada cenário de usuário é analisado a fim de extrair classes de análise, ou seja, entidades do domínio de negócio visíveis para o usuário. O documento de requisitos não deve incluir detalhes da arquitetura ou projeto do sistema.  Eles podem ser usados como parte do contrato para a implementação do sistema e devem consistir em uma especificação completa e detalhada de todo o sistema.

```ad-tip
##### Modelo Conceitual
É uma representação abstrata das entidades, conceitos e relações importantes em um determinado domínio de aplicação. Ele descreve os conceitos fundamentais que são relevantes para o sistema que está sendo desenvolvido, independentemente de como o sistema será implementado.

- É definido no processo de elicitação de requisitos.
```
#### Requisitos de Usuário
São abstratos, mais gerais e de alto nível. São declarações, em uma linguagem natural com diagramas, de quais serviços o sistema
deverá fornecer a seus usuários e as restrições com as quais este deve operar.
#### Requisitos de Sistema
Expressam a descrição mais detalhadas das funções, serviços e restrições operacionais do sistema de software. O documento de requisitos do sistema (às vezes, chamado especificação funcional) deve definir exatamente o que deve ser implementado. 
#### Requisitos Funcionais (o que deve ser feito)
São declarações de serviços que o sistema deve fornecer, de como o sistema deve reagir a entradas específicas e de como o sistema deve se comportar em determinadas situações. Em alguns casos, os requisitos funcionais também podem explicitar o que o sistema não deve fazer.

- Descrevem detalhes mais específicos como funções do sistema, suas entradas e saídas, exceções etc.
- A especificação dos requisitos funcionais de um sistema deve ser completa e consistente.
- Exemplos disso incluem processar pagamentos, gerar relatórios ou autenticar usuários.
#### Requisitos Não Funcionais (como deve ser feito)
São restrições aos serviços ou funções oferecidos pelo sistema. Incluem restrições de timing, restrições no processo de desenvolvimento, propriedades emergentes e restrições impostas pelas normas. Ao contrário das características individuais ou serviços do sistema, os requisitos não funcionais, muitas vezes, aplicam-se ao sistema como um todo.

- Eles podem estar relacionados às propriedades emergentes do sistema, como confiabilidade, tempo de resposta e ocupação de área.
- Um único requisito não funcional, tal como um requisito de proteção, pode gerar uma série de requisitos funcionais relacionados
-  São frequentemente mais críticos que requisitos funcionais individuais. 
- Como exemplo, a **interoperabilidade**, que é a capacidade do sistema de se comunicar e operar com outros sistemas, é um exemplo de requisito não funcional.
- Sempre que possível, os requisitos não funcionais devem ser escritos quantitativamente, para que possam ser objetivamente testados. 
##### Requisitos de Produto
Esses requisitos especificam ou restringem o comportamento do software. É um requisito de disponibilidade que define quando o sistema deve estar disponível e o tempo diário permitido de seu não funcionamento. Exemplos incluem os requisitos de desempenho quanto à rapidez com que o sistema deve executar e quanta memória ele requer, os requisitos de confiabilidade que estabelecem a taxa aceitável de falhas, os requisitos de proteção e os requisitos de usabilidade.
 ## Exemplo Real
 O MHC-PMS deve estar disponível para todas as clínicas durante as horas normais de trabalho (segunda a sexta-feira, 8h30 às 17h30). Períodos de não operação dentro do horário normal de trabalho não podem exceder cinco segundos em um dia.
##### Requisitos Organizacionais
Esses são os requisitos gerais de sistemas derivados das políticas e procedimentos da organização do cliente e do desenvolvedor. Exemplos incluem como os usuários se autenticam para o sistema, os requisitos do processo operacional que definem como o sistema será usado, os requisitos do processo de desenvolvimento que especificam a linguagem de programação, o ambiente de desenvolvimento ou normas de processo a serem usadas, bem como os requisitos ambientais que especificam o ambiente operacional do sistema.
 ## Exemplo Real
 Usuários do sistema MHC-PMS devem se autenticar com seus cartões de identificação da autoridade da saúde.
##### Requisitos Externos
Esse tipo abrange todos os requisitos que derivam de fatores externos ao sistema e seu pro- cesso de desenvolvimento. Podem incluir requisitos reguladores, que definem o que deve ser feito para que o sistema seja aprovado para uso, por um regulador, tal como um banco central; requisitos legais, que devem ser seguidos para garantir que o sistema opere dentro da lei; e requisitos éticos, que asseguram que o sistema será aceitável para seus usuários e o público em geral.
 ## Exemplo Real
 O sistema deve implementar as disposições de privacidade dos pacientes, tal como estabelecido no HStan-03-2006-priv.

![[engs-req-nf.png]]
#### Requisitos Voláteis
Durante o processo de levantamento e análise, alguns requisitos podem mudar ou surgir devido a diversos fatores, como o aumento do entendimento sobre o sistema por parte dos stakeholders, mudanças no mercado ou na legislação.
- Requisitos mutáveis: Requisitos que se modificam por causa do ambiente do sistema.
-  Requisitos emergentes: Requisitos que surgem à medida que a compreensão do cliente do sistema se desenvolve
-  Requisitos consequentes: Requisitos que resultam da introdução do sistema de computador.
- Requisitos de compatibilidade: Requisitos que dependem de outros sistemas ou processos de negócio específicos dentro da organização.
#### Estrutura de um Documento de Requisitos
![[engs-req-dr.png]]
#### Processos 
Podem incluir quatro atividades de alto nível:
##### Estudo de Viabilidade 
Elas visam avaliar se o sistema é útil para a empresa.
##### Elicitação e Análise
Visam descobrir requisitos. A elicitação e análise de requisitos podem envolver diversos tipos de pessoas em uma organização para obter informações sobre o domínio da aplicação, os serviços que o sistema deve oferecer, o desempenho do sistema, restrições de hardware e assim por diante.
1. Descoberta de requisitos do sistema.
2. Classificação, agrupação e organização de requisitos.
3. Priorização e negociação de requisitos.
4. Especificação de requisitos. 

![[engs-req-ela.png]]
##### Especificação
Converte os requisitos em alguma forma-padrão de documentação das funcionalidades e restrições do software. Este processo é essencial para dar direção ao desenvolvimento e garantir que o produto final atenda às expectativas.
##### Validação
Verificar se os requisitos realmente definem o sistema que o cliente quer. Ela se sobrepõe à análise, uma vez que está preocupada em encontrar problemas com os requisitos. A validação de requisitos é importante porque erros em um documento de requisitos podem gerar altos custos de retrabalho quando descobertos durante o desenvolvimento ou após o sistema já estar em serviço.
#### Técnicas para o Levantamento de Requisitos
##### Questionário
Adequada para situações onde os usuários estão dispersos geograficamente ou quando se busca obter dados quantificáveis de um grande número de pessoas. Essa abordagem é eficiente em coletar informações de forma estruturada, permitindo análises estatísticas e uma compreensão abrangente das necessidades dos usuários.
##### Etnografia 
Técnica de observação que pode ser utilizada para compreender os requisitos sociais e organizacionais, ou seja, entender a política organizacional bem como a cultura de trabalho com objetivo de familiarizar-se com o sistema e sua história. O analista se insere no ambiente de trabalho em que o sistema será utilizado. O trabalho diário é observado e são anotadas as tarefas reais em que o sistema será utilizado. O principal objetivo da etnografia é que ela ajuda a descobrir requisitos de sistema implícitos, que refletem os processos reais, em vez de os processos formais, onde as pessoas estão envolvidas.
##### Prototipagem 
Tem por objetivo explorar aspectos críticos dos requisitos de um produto, implementando de forma rápida um pequeno subconjunto de funcionalidades deste produto. O protótipo é indicado para estudar as alternativas de interface do usuário; problemas de comunicação com outros produtos; e a viabilidade de atendimento dos requisitos de desempenho.
##### Entrevistas
Convém que o entrevistador dê margem ao entrevistado para expor as suas idéias. É necessário ter um plano de entrevista para que não haja dispersão do assunto principal e a entrevista fique longa, deixando o entrevistado cansado e não produzindo bons resultados.

- Requer interação direta e pode ser custosa em termos de tempo e recursos se os entrevistados estiverem em locais distintos.