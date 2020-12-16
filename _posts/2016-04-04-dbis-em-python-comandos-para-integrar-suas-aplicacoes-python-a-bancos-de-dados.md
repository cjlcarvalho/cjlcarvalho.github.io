---
title: "Tutorial – DBIs em Python: Comandos para integrar suas aplicações Python a bancos de dados"
date: "2016-04-04"
---

Para explicar aos iniciantes em Python como funciona a integração dessa linguagem com SGBDs (Sistemas Gerenciadores de Banco de Dados), primeiramente preciso apresentar o que é e como funciona uma DBI.

Database Interface, ou DBI, é basicamente uma especificação que descreve como deve ser o comportamento de um módulo de acesso a sistemas de banco de dados, através de uma lógica de comunicação com o SGBD presente nesse banco.

A DBI define que o módulo deve ter uma função connect(), que retorna objetos de conexão. A partir desse objeto, é possível obter um cursor, que permite a executar consultas e sentenças SQL e obter a recuperação desses dados, que por padrão são retornados como uma lista de tuplas.

Entre os SGBDs mais conhecidos estão:

- MySQL
- SQL Server
- Firebird
- SQLite
- PostgreSQL
- Oracle
- MongoDB

Para integrar sua aplicação a esses bancos, é necessário que você baixe a DBI correspondente a ele através do Pip. Seguem abaixo os módulos/drivers mais utilizados:

- MySQL: pymysql, MySQLdb
- SQL Server: pyodbc, pymssql
- SQLite: sqlite3
- Firebird: firebirdsql, kinterbasdb, fdb
- PostgreSQL: postgresql,psycopg2, pypgsql
- Oracle: cx\_Oracle
- MongoDB: pymongo

Ao conectar ao seu banco de dados, é necessário utilizar a função connect(), como foi dito anteriormente, porém alguns SGBDs possuem parâmetros diferentes nessa função. Segue abaixo alguns exemplos de como conectá-los:

MySQL:

`con = pymysql.connect(host='servidor', db='teste', user='root', passwd='')`

SQLite:

`con = sqlite3.connect('teste.db')`

Firebird:

`con = firebirdsql.connect(host='servidor', database='banco.gdb', user='SYSDBA', password='masterkey')`

PostgreSQL:

`con = postgresql.open(host='servidor', database='teste', user='postgres', password='q1w2e3')`

SQL Server:

`con = pyodbc.connect('DRIVER={SQL Server};SERVER=servidor;DATABASE=banco;UID=user;PWD=password')`

Oracle:

`con = cx_Oracle.connect('usuario/senha@tnsname')`

MongoDB:

`client = MongoClient('servidor', 27017)` `db = client['teste']`

O objeto cursor é um apontador que faz o elo entre o código do Python e o seu banco de dados. Para criá-lo, basta utilizar uma variável qual quer que recebe o nome de sua conexão (na maioria dos exemplos acima foi utilizado 'con'), seguida de .cursor()

`cur = con.cursor()`

Agora para executar um comando, basta utilizar essa variável do cursor acompanhada de .execute(), utilizando como parâmetro uma string com o seu comando SQL.

`cur.execute('SELECT * FROM EXEMPLO')`

Para inserir valores personalizados nesse execute, entre com a sua string da sentença SQL e nos valores que você deseja personalizar, coloque uma interrogação (?) seguida por outro parâmetro que indica justamente os valores a serem atribuídos nessas interrogações.

`cur.execute('INSERT INTO TABELA(CAMPO1, CAMPO2) VALUES (?,?)', (valor1, valor2))`

Em muitos casos é necessário saber quantas linhas há no resultset do banco de dados. Para realizar este procedimento, uma variável qualquer recebe ‘nomeDoSeuCursor’.rowcount (no nosso caso, a variável que funciona como um cursor chamasse ‘cur’). Um exemplo bastante simples do número de linhas no resultset seria em um cadastro de contatos. Cada contato receberia, por exemplo, um nome, um endereço e um telefone. O número de contatos no BD seria equivalente ao número de linhas no resultset.

`x = cur.rowcount`

Para receber os resultados do database, criamos qualquer variável que recebe o nome do nosso cursor seguido de .fetchone() (que recebe um único resultado), .fetchall() (que recebe todos os resultados), etc. Vale lembrar que os resultados são recebidos como tuplas, como foi dito anteriormente.

`resultado = cur.fetchone()`

`resultado = cur.fetchall()`

`resultado = cur.dictfetchall()`

Para fazer uma alteração em seu banco de dados logo após executar o .execute(), basta utilizar o comando .commit() para salvá-las e não perder nenhum dado.

`con.commit()`

Quando um cursor não for mais necessário, é uma boa prática encerrá-lo. Para isto, basta colocar o nome do seu cursor seguido de .close().

`cur.close()`

E antes de fechar o seu programa que utiliza algum banco de dados, é interessante que a conexão com o seu BD seja encerrada. Para fazer isto, basta inserir no seu código a variável que recebeu a conexão com o database seguida de .close()

`con.close()`

Pronto, esses são alguns comandos e funções básicas das DBIs em Python para integrar de forma simples suas aplicações aos diversos SGBDs existentes no mercado.

**Referências:**

BORGES, Luiz Eduardo. **Python para Desenvolvedores.** São Paulo: Novatec, 2014.
