import sqlite3

conexao = sqlite3.connect('Dados')
cursor = conexao.cursor()

#1 Criação da tabela alunos
cursor.execute('CREATE TABLE alunos (id INT, nome TEXT, idade TEXT, curso TEXT);')

#2 Inserção de dados
cursor.execute('INSERT INTO alunos(id,nome,idade,curso) VALUES (1,"Isadora",23,"Engenharia")')
cursor.execute('INSERT INTO alunos(id,nome,idade,curso) VALUES (2,"Rodrigo",20,"História")')
cursor.execute('INSERT INTO alunos(id,nome,idade,curso) VALUES (3,"Lilian",19,"Engenharia")')
cursor.execute('INSERT INTO alunos(id,nome,idade,curso) VALUES (4,"Ana",21,"Letras")')
cursor.execute('INSERT INTO alunos(id,nome,idade,curso) VALUES (5,"Milena",20,"Ciência de Dados")')

#3 Consultas
a = cursor.execute('SELECT * FROM alunos')
for alunos in a:
    print(alunos)

b = cursor.execute('SELECT nome, idade FROM alunos WHERE idade > 20')
for alunos in b:
    print(alunos)

c = cursor.execute('SELECT * FROM alunos WHERE curso = "Engenharia" ORDER BY nome')
for alunos in c:
    print(alunos)

d = cursor.execute('SELECT COUNT(*) FROM alunos;')
for alunos in d:
    print(d)

#4 Atualização e remoção
cursor.execute('UPDATE alunos SET idade=22 WHERE nome="Isadora"')
cursor.execute('DELETE FROM alunos WHERE id = 4')

#5 Criação da tabela clientes e inserção de dados
cursor.execute('CREATE TABLE clientes (id INTEGER PRIMARY KEY, nome TEXT, idade TEXT, saldo REAL);')
cursor.execute('INSERT INTO clientes(id,nome,idade,saldo) VALUES (1,"João",20,"400.00")')
cursor.execute('INSERT INTO clientes(id,nome,idade,saldo) VALUES (3,"Carlos",35,"600.50")')
cursor.execute('INSERT INTO clientes(id,nome,idade,saldo) VALUES (5,"Fernanda",27,"300.00")')
cursor.execute('INSERT INTO clientes(id,nome,idade,saldo) VALUES (8,"Ricardo",25,"250.00")')
cursor.execute('INSERT INTO clientes(id,nome,idade,saldo) VALUES (9,"Jorge",24,"500.75")')

#6 Consultas
clientes_mais_30 = cursor.execute('SELECT nome, idade FROM clientes WHERE idade > 30')
for clientes in clientes_mais_30:
    print(clientes_mais_30)

saldo_medio = cursor.execute('SELECT AVG(saldo) FROM clientes')
for clientes in saldo_medio:
    print(saldo_medio)

clientes_saldo_maximo = cursor.execute('SELECT nome, MAX(saldo) FROM clientes')
for clientes in clientes_saldo_maximo:
    print(clientes_saldo_maximo)

clientes_saldo_alto = cursor.execute('SELECT COUNT(*) FROM clientes WHERE saldo > 1000')
for clientes in clientes_saldo_alto:
    print(clientes_saldo_alto)

#7 Atualização e remoção
cursor.execute('UPDATE clientes SET saldo=230.00 WHERE nome="Fernanda"')
cursor.execute('DELETE FROM alunos WHERE id = 3')

#8 Junção das tabelas
cursor.execute('CREATE TABLE compras (id INTEGER PRIMARY KEY, clientes_id INTEGER, produto TEXT, valor REAL, FOREIGN KEY (clientes_id) REFERENCES clientes(id));')
cursor.execute('INSERT INTO compras(clientes_id,produto,valor) VALUES (5,"Notebook",3500.00)')
cursor.execute('INSERT INTO compras(clientes_id,produto,valor) VALUES (9,"Impressora",600.00)')
juncao = cursor.execute('SELECT nome,produto,valor FROM clientes INNER JOIN compras ON clientes.id = compras.clientes_id')
resultados = juncao.fetchall()
for compra in resultados:
    print(compra)

conexao.commit()
conexao.close