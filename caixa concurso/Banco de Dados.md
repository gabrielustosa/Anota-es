# SGBD
#### Metadados 

São informações sobre o próprio banco de dados e seus elementos como: esquema do banco, dicionário de dados (informações sobre os tipos de dados armazenados em cada tabela), estatísticas de desempenho, privilégios e permissões, logs e registros. 
# DER (Diagrama Entidade Relacionamento) 

``` mermaid
flowchart LR
b["B1 (0, 1)"] --- rel{Relacionamento} --- a["(1, n) B2"]

```
- B1 precisa ter 1 ou vários relacionamentos com B2
- B2 pode ter nenhum um somente um relacionamento com B1

 **Total**: significa que para cada ocorrência da entidade genérica, existe sempre um ocorrência em uma das entidades especializadas
 **Exclusiva**: significa que uma ocorrência da entidade genérica A é especializada no máximo uma vez, ou seja, uma instancia de A aparece apenas uma vez nas entidades B ou C, nunca em ambas ao mesmo tempo.
# Normalização

- Cada forma normal depende das anteriores estarem sendo cumpridas.

 #### 1 FN
 Apenas valores atômicos, não há grupos repetidos, existe uma chave primaria, não possui atributos multivalorados, compostos ou relações aninhadas (uma tabela dentro da outra).
 #### 2 FN
 Conceito de dependência funcional, somente se cada atributo de R não-chave for total dependente da PK de R, válido somente se R tiver um chave primária composta.
 #### 3 FN
 Baseada no conceito da dependência transitiva, não deve haver dependência de uma coluna a chave primaria e a outro campo na coluna.
 #### 4 FN 
 Não pode conter dependências multivaloradas.
 #### 5 FN
 Dependência de junção. Quando uma tabela T pode ser decomposta em outras tabelas como T1, T2, T3
# Conceitos 

 #### CONCEITUAL
 Definição de user-views, saída, requerimentos, diagramas (relacionamento, entidades, atributos).
 #### LÓGICO
 Definição das tabelas, colunas, relacionamentos, verificação de normalizações e integridade.
 #### FÍSICO
 Definição de tabelas, views, indexes que estão relacionados com a parte física do armazenamento.
#### ACID 
 ##### Atomicidade 
 Garante que todas as alterações realizadas por uma transação serão efetivadas no banco de dados, ou nenhuma delas, caso ocorra algum problema. Ou seja, não há atualização parcial da transação. 
 ##### Consistência
 Nesse caso é garantido que novas transações somente serão completadas se elas não ferirem nenhuma regra do banco de dados que possa torná-lo inconsistente. 
 ##### Isolamento
 Propriedade que permite que os eventos em uma transação não interfiram nos eventos de outra transação concorrente. 
 ##### Durabilidade
 Garante que o resultado de toda transação executada com sucesso deverá ser mantido no banco de dados, mesmo na ocorrência de falhas.
# SQL

 #### DDL (DATA DEFINITION LANGUAGE) 
 Create, Drop, Truncate, Rename, Alter, Constraint
 #### DML (DATA MANIPULATION LANGUAGE)
 Select, Where, And, Or, Not, Order By, Insert, Update, Delete, Limit 
#### Join
Um **Join**, também conhecido como **Inner Join**m combina resultados de diferentes tabelas baseado em colunas que estão relacionadas.

```sql
SELECT u.first_name, u.salary, r.name 
FROM users u 
JOIN users_roles ur ON u.id = ur.user_id 
JOIN roles r ON ur.role_id = r.id;
```

#### Left/Right (Outter) Join  
Usado para retornar todos os resultados que estão relacionados pela chave além de trazer todos os resultados do lado esquerdo/direito da junção que apresentam valores nulos. 

```sql
SELECT u.first_name, u.salary, p.bio
FROM users u 
LEFT ou RIGHT JOIN profiles p ON u.id = p.user_id;
```

#### Full (Outter) Join
Usado para retornar todos os resultados de ambas as tabelas com os valores que não combinam preenchidos com null.

```sql
SELECT u.first_name, u.salary, p.bio
FROM users u 
FULL JOIN profiles p ON u.id = p.user_id;
```

#### Group By 
Agrupa resultados com base em uma coluna. (Geralmente utilizado com funções de agregação)

```sql
SELECT r.name, COUNT(u.id) 
FROM users u
JOIN users_roles ur ON ur.user_id = u.id
JOIN roles r ON r.id = ur.role_id 
GROUP BY r.name;
```

#### Having
Existe pois o **WHERE** não pode ser usado dentro de funções de agregação, como o Group By. 

```sql
SELECT r.name, COUNT(u.id) 
FROM users u
JOIN users_roles ur ON ur.user_id = u.id
JOIN roles r ON r.id = ur.role_id 
GROUP BY r.name
HAVING r.name NOT LIKE 'c%';
```

#TODO **Metadata Management**, **Concurrency Control**, **Query Optimization**, **Indexing**, **Storage Management**

