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

## Tipos de campos para um BDD Oracle

### Campos Textos
1. **CHAR** - Armazena cadeias de caracteres de comprimento **fixo**. Campo com limite de **1 a 2000 caracteres**. Se criarmos um CHAR(10) e inserirmos um texto com 5 caracteres, o oracle preenche os outros 5 com espaços em branco. **Se o texto inserido for maior que o limite, haverá um retorno de erro.**
2. **VARCHAR, VARCHAR2** - Armazena cadeias de caracteres de comprimento **variável**. Campo com limite de **1 a 4000 caracteres**. Se criarmos um VARCHAR(10) e inserirmos um texto com 5 caracteres, o oracle preenche apenas os 5 caracteres que inserimos. **Use sempre VARCHAR2.** O VARCHAR usa uma tabela ANSI, já o VARCHAR2 usa uma tabela interna da Oracle. **Se o texto inserido for maior que o limite, haverá um retorno de erro.**
3. **NCHAR, NVARCHAR, NVARCHAR2** - Armazena cadeias de caracteres de comprimento fixo ou variável, mas **são caracetres UNICODE** (englobam quase todos os caracteres do mundo). Respeita as caracteristicas do CHAR, VARCHAR e VARCHAR2.
4. **CLOB, NLOB** - São campos longos que podem armazenar até 8 TB de dados por campo. Correspondem a **VARCHAR2 e NVARCHAR2**.
5. **LONG** - Não deve ser mais usado nas versões atuais. Só continua existindo por causa de bancos Oracle antigos. 
### Campos Numéricos
1. **NUMBER** - Armazena números de tamanho fixo e de ponto flutuante. Qualquer número pode ser armazenado neste campo até 38 dígitos de precisão. **Opcionalmente**, podemos determinar a precisão incluindo a escala e a precisão. Ex: NUMBER(10,2) -> 10 digitos, 2 digitos após a casa decimal.
2. **INTEGER, SHORTINTEGER, LONGINTEGER, DECIMAL, SHORTDECIMAL** 
### Campos Datas
1. **DATE** - Armazena dados no formato Data e Hora. Pode armazenar datas Julianas de 1 Janeiro de 4712 AC a 31 de Dezembro de 9999 DC. A forma de armazenar data da Oracle é DD-MM-YY. 00:00:00AM é o padrão da hora caso não seja explictamente especificado. 
2. **TIMESTAMP, TIMESTAMP WITH TIME ZONE, TIMESTAMP WITH LOCAL TIME ZONE** - Tipos especiais que levam em conta milésimos de segundos, fuso horários e, inclusive, horário de verão.
### Campos Binários
1. **BLOB** - Armazena dados binários não estruturados no banco de dados. BLOBs pode armazenar até 128 TB de dados binários. 
2. **BFILE** - Armazena dados binários não estruturados em arquivos do sistema operacional fora do banco de dados.

### Importante notar que o Oracle não trabalha com booleano, então usa-se Number(1), onde 0 é falso e 1 é verdadeiro

## Criação de Tabelas

```
CREATE TABLE TB_CLIENTES (
	CPF VARCHAR2(11),
	NOME VARCHAR2(100),
	ENDERECO1 VARCHAR2(150),
	ENDERECO2 VARCHAR2(150),
	BAIRRO VARCHAR2(50),
	CIDADE VARCHAR2(50),
	ESTADO CHAR(2),
	CEP CHAR(8),
	DATA_NASCIMENTO DATE,
	IDADE INTEGER,
	SEXO CHAR(1),
	LIMITE_CREDITO NUMBER(15,2),
	VOLUME_COMPRA NUMBER,
	PRIMEIRA_COMPRA NUMBER(1)
);
```