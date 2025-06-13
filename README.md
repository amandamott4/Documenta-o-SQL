# Documentação SQL
Descriçao de termos e exemplificação de comandos SQL(Structured Query Language)


TERMOS e COMANDOS SQL

sempre use ; no final dos comandos
TIPOS DE DADOS:
int -> número inteiro 
decimal (m,d)  -> número decimal com (m) dígitos e (d) casas decimais varchar (n)  ->string(texto) de comprimento (n) 
date  -> data no formato: yyyy-mm-dd .

SQL: Structured Query Language (Linguagem de Consulta de dados), também conhecida como SEQUEL.

SGBD (Sistema Gerenciador de Banco de Dados): coleção de programas usados para acessar, guardar, criar e gerenciar os Banco de Dados, por meio da linguagem SQL.
EX: MySQL, ORACLE DATABASE, SQLite, SQL Server, PoatgreSQL
SGBDs podemos citar o modelo hierárquico, modelo em redes, modelo relacional (mais utilizado atualmente) além do modelo orientado a objetos.

BD/DB: Database (Banco de Dados) ou SCHEMA

DBA:  Database Administrator (Adminidtrador de banco de dados)

CRUD: CREATE, READ, UPDATE, DELETE

ACID:  Atomicidade, Consistência, Isolamento e Durabilidade. São propriedades das transações em bancos de dados (como INSERT, UPDATE e DELETE)


DML (Data Manipulation Linguagem): Linguagem de Manipulação de Dados, é um conjunto de comandos para manipulação dos dados armazenados dentro das tabelas em um banco de dados: INSERT – UPDATE - DELETE

insert into nome_tabela values (‘dado1’ , ‘dado2’ , ‘dado3’ ) 
:inserindo dados nas tabelas

     PROJEÇÃO
é tudo que você quer ver na tela, o que será projetado, construído para ser mostrado(select)
SELEÇÃO
é um subconjunto do conjunto total de registros de uma tabela
a cláusula de seleção é o where
 quando seleciona o que vai ver, quando filtra
JUNÇÃO(Inner Join)
quando junta duas ou mais tabelas
é como se estivesse colocando os ids(em comum) para combinar as tabelas
em um relacionamento 1xN: o relacionamento 1 irá se repetir conforme a quantidade de registros no N.


select nome_coluna, nome_coluna, nome_coluna
from nome_tabela
inner join nome_outra_tabela
on idcoluna = id_outracoluna;
:unir colunas especificas de tabelas diferentes


nesse caso uma boa prática é atribuir alias para abreviar o tamanho do codigo e mante-lo mais clean, por exemplo:
select c.nome, c.sexo, e.bairro, e.cidade, t.tipo, t.numero
from cliente c
inner join endereco e 
on c.idcliente = e.id_cliente
inner join telefone t 
on c.idcliente = t.id_cliente;


UPDATE
ao atualizar um dado é importante que sempre utilize a clausula WHERE, e se sertificar que é realmente esse dado a ser atualizado, geralmente usando o ID da coluna.
SET= indica qual será a alteração, e o WHERE indica onde.
update nome_tabela set _nome_coluna que será atualizada = novo_dado where id_coluna = dado_antigo 
 :atualizando dados nas tabelas


DELETE
segue a mesma logica de cuidado que o update, certifique-se de que é realmente esse dado que deseja apagar.


delete from nome_ tabela where nome_coluna = dado  
:deletar dados nas tabelas 


DDL (Data Definition Language) Linguagem de Definição de Dados, é usada para criar e modificar a estrutura dos objetos armazenados em um banco de dados: ALTER – CREATE – DROP. 

CREATE TABLE
cria uma tabela e descreve a descrição dela, seguindo a ordem: nome_tabela, e depois a descrição das colunas, seguindo a ordem: nome_coluna tipo…
ALTER TABLE
use CHANGE para alterar o nome da coluna 
use MODIFY para alterar o tipo
use ADD para adicionar uma coluna
first=  para ir para a primeira coluna
after=  depois de  uma coluna para uma ordem específica
use DROP COLUMN para eliminar uma coluna
DROP
drop table nome_tabela :excluir tabelas e banco de dados

DQL (Data Query Language) Linguagem de Consultade Dados, são os comandos de consulta aos dados armazenados em um bando de dados: SELECT
select * from nome_tabela
 :visualizar todas as colunas de uma tabela

select coluna1, coluna2 from tabela 
: visualizar colunas específicas de uma tabela

select * from tabela  limit  número 
:restringir o número de item que são retornados da sua consulta

select * from tabela where coluna =  ‘número/texto/data’ 
:aplicar filtro na consulta

select * from tabela where coluna =  ‘número/texto/data’ and / or coluna =  ‘número/texto/data’
 :aplicar dois filtros ao mesmo tempo

select count (nome_coluna) from nome_tabela
:quantidade total de linhas de uma coluna

select count(*) from tabela :total de linhas,inclui os nulos

select count(distinct nome_coluna) from nome_tabela 
:contagem de dados diferentes por coluna


select sum(nome_coluna) from nome_tabela
:calcula o total dos dados de uma coluna

select avg(nome_coluna) from nome_tabela 
:calcula média dos valores de uma coluna

select min(nome_coluna) from nome_tabela 
:encontrar o menor valor de uma coluna


select max(nome_coluna) from nome_tabela  
:encontrar o maior valor de uma coluna

select nome_coluna from nome_tabela group by nome_coluna 
:agrupar

select * from tabela order by nome_coluna asc / desc
:ordenar de forma crescente ou decrescente

DCL (Data Control Language): Linguagem de Controle de Dados, é usada para controle de acesso e permissões dos usuários em um banco de dados: GRANT – REVOKE - DENY

TCL (Transaction Control Language): linguagem de Controle de Transação, são comandos usados para gerenciar as mudanças feitas pelos comandos DML: COMMIT – ROLLBACK – SAVEPOINT.

ALIAS é um nome temporário atribuído a uma coluna ou tabela dentro de uma consulta, geralmente é a primeira letra da coluna/tabela ou abreviação dela.

TABLE; é formado por linhas e colunas que armazenam dados que podem ser consultados sempre que quisermos.

TABELA DIMENSÃO= características de um elemento ‘‘produtos, funcionários, clientes’’ é onde fica a Chave Primária

TABELA FATO= fatos acontecidos em determinado período de tempo ‘‘vendas, devoluções, receitas’’ é onde fica a Chave estrangeira.

Na linguagem do modelo relacional, cada linha é chamada de tupla, a coluna ou cabeçalho é chamado de atributo e a tabela de relação. Desta maneira, o conjunto de nomes das tabelas e suas colunas são chamados de esquema da relação.


CARACTERES= Alfa-numéricos ou símbolos.
CAMPO= Coleção de Caracteres;
REGISTRO= Coleção de Campos (Tuplas)
ARQUIVOS= Coleção de Registros;
BANCO DE DADOS= Coleção de Arquivos;

MER: (Modelo Entidade Relacionamento)
DER: (Diagrama Entidade Relacionamento) representação gráfica do MER

MODELAGEM DE DADOS: é o processo de criar uma representação visual/diagrama
ETAPAS DA MODELAGEM DE DADOS:
1.Entendimento do problema
2.MER
3.DER
4.N:N
5.Definição do Modelo lógico
6.Normalização das tabelas
7.Documentação
8.implementação do Modelo físico

OPERADOR LÓGICO: termo auxiliar do WHERE para refinar mais ainda a query
AND: retorna true se todas as condições forem verdadeiras.
OR: retorna true se pelo menos uma das condições for verdadeira.
NOT: para excluir um valor
IN: verifica se uma valor está dentro da lista descrita
NOT IN: para excluir múltiplos valores:
LIKE: busca valores parecidos com "escreva_a_palavra%".
NOT LIKE: retorna todos os resultados exceto aqueles cujo nome começa com "escreva_a_palavra%".	
IS NULL: verifica se um valor é nulo
EXISTS: verifica se uma subconsulta retorna algum resultado
BETWEEN: verifica se o valor está entre dois resultados, geralmente entra datas

CARDINALIDADE= a forma como as entidades se relacionam.
Elas podem ser: 1:1  -> um para um
 1:N -> um para muitos
N:N -> muitos para muitos      

CONSTRAINT= restrição aos dados para que seja íntegro e  consistente. 
EX:  	not null
unique
primary key 
foreign key
check

CHAVE  PRIMÁRIA= ID, um campo que identifica de forma única cada registro em uma tabela
AUTO_INCREMENT= gera automaticamente valores únicos para uma coluna, geralmente usada como chave primária

CHAVE ESTRANGEIRA= é a chave primária de uma tabela que vai até a outra coluna para fazer referência entre registros. 
 -Em relacionamento 1 x 1 a chave estrangeira fica na tabela mais fraca .
 -Em relacionamento 1 x n a chave estrangeira ficará sempre na cardinalidade n .


-foreign key(id_nomeTabelaPrimaria)
references      nomeTabelaPrimaria(idnomeTabelaPrimaria)



UNIQUE= essa restrição é usada para garantir que os valores em uma coluna ou conjunto de colunas sejam únicos dentro de uma tabela. Isso significa que nenhum valor duplicado pode ser inserido nessas colunas

NOT NULL= garante que uma coluna em uma tabela não possa conter valores nulos (vazios).
CHECK=  sobre os valores que podem ser inseridos em uma coluna, por exemplo, se você quiser garantir que a idade de uma pessoa seja sempre 18 anos ou mais.
     
RESTRIÇÃO DE INTEGRIDADE= regras de consistência de dados, para evitar erros humanos
     -Integridade e Vazio: Informa se os valores da coluna são opcionais ou não
     -Integridade de Chave: Valores em uma chave primária não devem ser nulos.
     -Integridade Referencial: Valores de uma coluna em uma tabela são válidos baseados nos valores em outra tabela relacionada

FORMAS NORMAIS: um passo a passo para garantir que as tabelas estejam estruturadas e atualizadas.




Banco de Dados
show databases :mostrar todas as databases criadas
use nome_database :usar a db selecionada
create database nome_db :criar banco de dados
drop database nome_banco :excluir banco de dados



Tabela
create table nome_tabela(
    nome_coluna tipo_dado(quantidade_dado)
);
:criar tabela e colunas

alter table nome_tabela
change nome_tabela_antigo nome_tabela_novo tipo;
:altera a descrição da tabela, como o nome da coluna 

alter table nome_tabela
modify nome_tabela novo_tipo;
:altera o tipo
delete from nome_tabela :apagar apenas os dados de uma tabela 


show tables :mostrar as tabelas dentro do db selecionado
desc nome_tabela :mostrar colunas de uma tabela



Subqueries
select * from nome_tabela where nome_coluna > (select avg(nome_coluna) from nome_tabela
:criação de subqueries(resultado de uma consulta dentro de outra consulta):  
 
 
 Trigger  
select trim(to_char(sysdate, 'day')) from dual; --dia atual 
:criação de trigger (um gatilho que será disparado automaticamente quando acontecer um evento)


Views 
create view nome_view as
(resto da query)
:é uma possibilidade de armazenar o resultado de uma query e acessar apenas com o nome dela
é interessante usar um prefixo antes de todas as views para facilitar a busca,
ex: vw_nome_view
alem disso é possivel fazer uma query usando a view, se quiser fazer uma pesquisa mais enchuta e aplicar select em apenas algumas colunas daquela view.

create or alter view nome_view as  
select * from tabela 
where coluna = ‘novos dados na coluna’ 
:alterar view


drop view nome_view  
:excluir view


	select now() as data_atual;
	:retorna data e hora no momento da busca


IFNULL
SELECT  C.NOME, 
		IFNULL(C.EMAIL,'NAO TEM EMAIL') AS "E-MAIL",
		E.ESTADO, 
		T.NUMERO
FROM CLIENTE C
…
:é uma função que substitui valores NULL por um valor especificado.
