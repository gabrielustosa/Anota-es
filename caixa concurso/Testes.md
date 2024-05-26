```ad-summary
Teste de caixa preta: Teste de aceitação, teste de sistema, teste de integração.
Teste de caixa branca: Teste de unidade, teste de integração detalhado.
```
# TDD
O Test Driven Development (**TDD**) é uma técnica de desenvolvimento de software que enfatiza a escrita de testes automatizados _antes_ da implementação do código de produção. O processo é iterativo e envolve três fases principais: **Red**, **Green** e **Refactor**. No estágio **Red**, escreve-se um teste que falha, pois a funcionalidade ainda não foi implementada. Em **Green**, escreve-se o código necessário para fazer o teste passar. E em **Refactor**, refatora-se o código para melhorar sua qualidade sem alterar seu comportamento.


![[testes-tdd.png]]

TDD se baseia em ciclos _curtos e rápidos_ de desenvolvimento, onde o teste é escrito _antes_ do código de produção, direcionando assim o desenvolvimento da funcionalidade.
# Teste de Regressão
É realizado a qualquer momento no projeto do sistema por não ter necessariamente alguma posição na sequência de realização do teste. Consiste em reexecutar testes após alguma alteração no sistema verificando se tudo está funcionando corretamente.
#### Características
Implementar testes automáticos fazem a diferença por serem codificados por um programador apenas apertando um botão, todos os testes são executados automaticamente poupando tempo e trabalho para a realização do teste manual.

- Testes de regressão podem ser caros ou baratos dependendo da forma como o testador utiliza o teste, sendo ele manual ou automático.
# Testes de Aceitação
Este tipo de teste é crucial porque representa a validação do software pelos usuários finais. O objetivo central dos testes de aceitação é garantir que o software atenda às necessidades e exigências dos usuários, de acordo com o que foi estabelecido nos requisitos de implementação.

```ad-summary
##### Testes de Sistema
São realizados pela equipe de testes, visando a execução do sistema como um todo ou um subsistema (parte do sistema), dentro de um ambiente operacional controlado, para validar a exatidão e perfeição na execução de suas funções. Neste estágio de testes deve ser simulada a operação normal do sistema, sendo testadas todas as suas funções de forma mais próxima possível do que irá ocorrer no ambiente de produção. São usados dados de teste e situações de teste de modo a tentar evitar a ocorrência de defeitos em ambiente de produção.
```
### Processo de Aceitação de Software
1. Definir Critérios de aceitação
2. Planejar testes de aceitação
3. Derivar testes de aceitação
4. Executar testes de aceitação
5. Negociar resultados de testes 
6. Aceitar ou rejeitar sistemas.
## Aceitação Formal
O teste de aceitação formal é um processo altamente gerenciado e costuma ser uma extensão do teste do sistema. Os testes são planejados e projetados com o mesmo cuidado e nível de detalhe do teste do sistema. Os casos de teste escolhidos devem ser um subconjunto dos que foram realizados no teste do sistema. É importante não se distanciar de nenhuma forma dos casos de teste escolhidos.
#### Características
Realizada em um ambiente controlado, com base em critérios de aceitação predefinidos e documentados. Pode ser automatizada ou manual.
- Principal foco é nos critérios de aceitação
## Aceitação Informal (Teste Alfa)
Usa o sistema de forma não planejada disponibilizando o sistema para um pequeno grupo de pessoas. Essas pessoas participam do projeto dando feedbacks sobre a situação atual em que o sistema se encontra. O teste alfa é frequentemente usado para sistemas de prateleira como forma de teste de **aceitação interna**.
#### Características
O grupo que participa dos testes geralmente é composto por membros da organização e também do cliente.

- Esse teste visa a identificação de possíveis erros não identificados sendo analisados por uma quantidade de usuários que desfrutam do sistema.
- É conduzido na instalação do desenvolvedor com o time de programadores acompanhando os testes para coletar dados de falhas a serem corrigidas e melhorias a serem aplicadas.
## Teste Beta
Realizado por um grande número de pessoas, a execução do sistema ocorre de forma não planejada por pessoas desconhecidas, que não possuem nenhuma relação com a equipe ou empresa desenvolvedora. Frequentemente o teste é utilizado como uma forma de **aceitação externa** para **softwares de prateleira** possibilitando avaliar o **feedback** do mercado.
#### Características
Os usuários finais testam o software em um ambiente de produção, mas a implantação ainda é considerada uma "pré-lançamento".

- Os programadores não farão acompanhamento do sistema porque nesse teste são conduzidos nas instalações dos usuários finais que irão reportam os erros encontrados.
- Foco na busca de defeitos e análise da experiência do usuário.

