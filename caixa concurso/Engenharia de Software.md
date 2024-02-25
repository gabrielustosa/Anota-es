# Processo Unificado 

Um conjunto de atividades executadas para transformar um conjunto de requisitos do cliente em um sistema de software.

- É baseado em componentes que utilizam interfaces.
- Utiliza toda uma definição em UML.
- Dirigido por casos de usos
- Centrado na arquitetura, Interativo e incremental

 ###### Arquitetura
 É um "mapa" do sistema, definindo partes do mesmo como relacionamentos, iterações, mecanismos. implementação, distribuição. É fundamental para entender a visão global, as possibilidades de reuso e evolução do sistema. 
 ###### Iterativo e incremental
 O software não é implementado a partir de um instante no fim do projeto, o ciclo de vida no PU é implementado em iterações.
 ###### Iterações
 É um miniprojeto que resulta em uma versão do sistema liberada interna ou externamente. Essa versão oferece uma melhora incremental sobre a interação anterior. 
#### Ciclo de Vida

Formado por 4 fases: **Concepção (Inception), Elaboração (Elaboration),  Construção (Construction) e Transição (Transition)**.
Cada fase, é subdivida em iterações que passam por todos os cinco fluxos do trabalho do processo: **Requisitos, Análise, Implementação e Testes**.

- Não se comporta como modelo de cascata, os fluxos de trabalho podem ser realizados a qualquer momento durante o ciclo de desenvolvimento.
- Disciplinas podem ter mais ênfase do que outras.

 ##### CONCEPÇÃO
 Estabelece a viabilidade do sistema proposto, definido os casos de usos mais importantes que delimitam o domínio do sistema, além disso é definido o escopo, custos, cronograma, potenciais riscos e esboço do projeto.
 ##### ELABORAÇÃO
 Capturar o que pode ser feito com as restrições financeiras e outras questões levantadas, captura dos requisitos funcionais, expansão do esboço, abordagem dos riscos significativos, elaboração de um plano econômico  na fase de construção. Ampliação dos casos de uso e da arquitetura. Tem como resultado o conjunto dos modelos junto com os elementos de implementação
 ##### CONSTRUÇÃO
 As iterações estão voltadas para a produção de código. Tendo como resultado um produto estável, ainda que possa ser aperfeiçoado. 
 ##### TRANSIÇÃO
 Período em que o produto passa para beta-teste. Envolve atividades de treinamento de usuários, assistências de uso e correções de defeitos.
 

#### 4 Ps (Pessoa, Projeto, Produto e Processo)

 ##### PESSOAS
 Financiam, escolhem, desenvolvem, gerenciam, testam, usam e são beneficiadas pelo produto.
 ##### PROJETOS
 Sofrem alterações. Determinam os tipos de pessoas que irão trabalhar no projeto e os **artefatos** que serão usados.
 ##### PRODUTO
 Código fonte, diagramas e outros artefatos
 ##### PROCESSO
 Define **quem (papel/pessoa/trabalhadores)** faz **o que (artefato)**, **quando (disciplina)** e **como (atividades)**
 
 ###### Artefato
 É qualquer tipo de informação criada por uma pessoa (diagramas UML, textos, modelos, interfaces)
 ###### Trabalhadores
 Responsável pela produção ou modificação de artefatos; Exemplos (programador, analista, testador)
 ###### Atividades
 Tarefa que o trabalhador executa afim de produzir ou modificar um artefato.
 ###### Disciplina
 Descreve as sequências das atividades e as iterações com que participa, sendo realizadas a qualquer momento do ciclo.

#### Casos de usos

Um caso de uso é uma sequência de ações, executada por atores que produzem um ou mais resultados de valor para outros atores.

- Possibilitam que os requisitos funcionais possam ser capturados na perspectiva de cada usuário do sistema.
- Os testes são baseados nos casos de usos.
- Os requisitos funcionais são expressões através dos casos de uso, que são adicionados a cada interação.

 ###### Atores
 É uma pessoa ou outro sistema

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
