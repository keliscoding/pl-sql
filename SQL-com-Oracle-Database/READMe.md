# SQL com Oracle Database
Este Readme trata-se do meu entendimento e anotações sobre alguns tópicos abordados durante as aulas de PL/SQL da Alura.  

## Conjuntos de Comandos

- DDL: Data Definition Language  
São comandos que permitem ao usuário especificar um esquema de banco de dados através de um conjunto de definições.  
Ex: CREATE, DROP, ALTER, TRUNCATE  

- DML: Data Manipulation Language  
São comandos que permitem ao usuário manipular dados de uma tabela no banco de dados.  
Ex: INSERT, UPDATE, DELETE, LOCK

- DCL: Data Control Language
São comandos que lidam com direitos, permissões e outros controles do sistema de banco de dados.  
Ex: GRANT, REVOKE

- DTL ou TCL: Transation Control Language
São comandos usados para gerenciar transações no banco de dados.
Ex: BEGIN/SET TRANSACTION, COMMIT, ROLLBACK, SAVEPOINT  

- DQL: Data Query Language
São comandos responsáveis pela consulta dos dados armazenados.  
Ex: SELECT

## Componentes do DB Oracle

### Tablespace

### Tabelas
- **Número de colunas/campos é limitado.** Associado a definição da tabela.
- **Número de linhas/registros** é quantos o espaço em disco comportar.
- Colunas possuem definições rígidas. O tipo deve ser único.
- **Chave Primárias** (não são obrigatórios). Colunas cujos valores não podem se repetir nas linhas da tabela. 
- **Chave Estrangeira**. Faz a ligação entre dois campos de duas tabelas diferentes. Os campos devem ter as mesmas propriedades. O campo no qual a chave estrangeira se liga deve ser uma chave primária.
- **Índice**. Ajuda afazer buscas mais ráoidas associadas aquela coluna. Toda chave primária vai ter um índice criado. Podemos ter colunas que não sejam chaves primárias, mas que tenham índices. **Uma tabela que tem muitos índices vai ficar mais lenta quanto tivermos que escrever algo nela.**

### Visão

-  As visões são como "tabelas lógicas". As visões não existem fisicamente no banco, mas conseguimos visualizá-las como se fossem uma tabela.

- Ao receber o resultado de uma consulta podemos torná-la uma view.

- Fazer consulta por visão tem uma performance pior do que fazer a consulta direto com a tabela.

### Procedures ou funções (PL/SQL)
- Muitas vezes, uma consulta não será resolvida somente com um comando de SQL direto na tabela. Pode ser preciso uma estrutura lógica programada através dessa linguagem de programação (no caso do Oracle, é o PL/SQL).

### Trigger
-  Trigger é uma regra que podemos criar no banco de dados para efetuar alguma coisa quando algo acontecer.