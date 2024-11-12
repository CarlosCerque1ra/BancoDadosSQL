# BancoDadosSQL

# Passo a passo: Criação de um banco de dados
Tutoria de como criar um banco de dados SQL que organiza as informações de 'livros', 'editora', 'autores' e 'assuntos'.
Este guia será dividido em etapas para demonstrar desde a criação de tabelas, chave e até manipulação/consulta de dados.
## Resumo da estrutura SQL
*__CREATE__ para criar 'Banco de dados' ou 'Tabelas'
*__ALTER__ para adicionar ou modificar colunas
*__DROP__ para remover 'Banco de dados' ou 'Tabelas'
*__INSERT__ para adicionar

## Passo 1: criação do Banco de Dados e das Tabelas
#### 1.1 Criando o DB

```SQL
CREATE DATABASE biblioteca;
USE biblioteca;
```

### 1.2 Criando a tabela 'editora'
```SQL
CREATE TABLE editora(
    id_editora INT PRIMARY KEY  AUTO_INCREMENT,
    nome_editora VARCHAR(100) NOT NULL,
    pais VARCHAR(50)
);
```

#### 1.3 Criando a tabela 'autor'
```SQL
CREATE TABLE autor(
    id_autor INT PRIMARY KEY  AUTO_INCREMENT,
    nome_autor VARCHAR(200),
    data_nascimento DATE
);
```

#### 1.4 Criando atabela 'assunto'
```SQL
CREATE TABLE assunto(
    id_assunto INT PRIMARY KEY  AUTO_INCREMENT,
    descricaio_assunto VARCHAR(500) NOT NULL,
);
```

#### 1.5 Crindo a tabela 'livro'
```SQL
CREATE TABLE livro(
    id_livro int PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(150) NOT NULL,
    editora int,
    autor int,
    assunto int,
    ano_publicacao YEAR,
    FOREIGN KEY(editora) references editora(id_editora),
	FOREIGN KEY(autor) references autor(id_autor),
	FOREIGN KEY(assunto) references assunto(id_assunto)
);
```

#### 1.6 Criando uma tabela EXTRA
A tabela vai servir para edificar a exclusão

```SQL
CREATE TABLE extra(
    id INT PRIMARY KEY AUTO_INCREMENT,
    produtos VARCHAR(50) NOT NULL,
    quantidade INT(20) NOT NULL,
    preco DOUBLE NOT NULL
);
```

## Passo 2: edificar usando 'ALTER'
Após a criação da tabela, podemos adiconar novos campos. Vamos adicionar uma coluna 'email' na tabela 'altor'

```SQL
ALTER TABLE autor
ADD COLUMN email VARCHAR(100);
```

## Passo 3: Remover tabela usando 'DROP'
Se precisar remover uma tabela usamos o comando 'DROP'.
Neste exemplo vamos remover a tabela 'extra'

```SQL
DROP TABLE extra;
```

## Passo 4: Inserindo dados usando 'INSERT'
Agora que as tabelas ja estão prontas, vamos inserir dados nelas.

### 4.1 Inserindo dados na tabela 'editora'
```SQL
INSERT INTO editora(nome_editora, pais)
VALUES
('Editora Alfa', 'Brasil'),
('Editora Beta', 'Portugal'),
('Editora Bertrand Brasil', 'Brasil');
```

#### 4.2 Inserindo Dados na tabela 'autor'
```SQL
INSERT INTO autor (nome_autor, data_nascimento, email)
VALUES
('Jorge Amado', '1912-08-10', 'jorginho@gmail.com'),
('Machado de Assis', '1839-06-21', 'machadinho@gmail.com'),
('Matt Haig', '1975-06-03', 'matt@gmail.com');
```

#### 4.3 Inserindo dados na tabela 'assunto'
```SQL
INSERT INTO assunto (descricao_assunto)
VALUES
('Ficção'),
('Mistério'),
('Terror'),
('Ação');
```

#### 4.4 Inserindo dados na tabela 'livros'
```SQL
INSERT INSERT livro(titulo, ano_publicacao, editora, autor, assunto)
VALUES
('Capitães de area', '1937', 1, 1, 5),
('Dom Casmurro', '1899', 2, 2, 5),
('A biblioteca da meia noite', '2020', 3, 3, 2),
('Memóras Póstumas de Brascubas', '1881', 1, 2, 5);
```

## Passo 5: Atualizando os dados usando 'UPDATE'
Podemos atualizar os dados com o comando UPDATE.
Vamos corrigir a data de publicação do livro 'Capitães de Areia'

```SQL
UPDATE livro
SET ano_publicacao = 1938
WHERE titulo = 'Capitães de Areia';
```

## Passo 6: Excluindo os dados usando 'DELETE'
Para remover os registros de uma tabela usamos o comando 'DELETE'.
Vamos excluir o livro 'Memórias Póstumas de Brás Cubas'.
```SQL
DELETE FROM livro
WHERE id_livro = 4;
```

## Passo 7: Consultando os dados usando 'SELECT'
É possível selecionar os dados para visualizar na forma como quiser.
Para isso usamos o comando 'SELECT'

#### Passo 7.1: Selecionar todos os livros com suas editoras e autores
Vamos usar dados das tabelas 'livros', 'editora', 'autor' e 'assunto' usando o comando 'JOIN'
```SQL
SELECT  livro.titulo AS nome, 
        editora.nome_editora AS editora,
        autor.nome_autor AS autor,
        assunto.descricao_assunto AS assunto,
        livro.ano_publicacao AS ano
FROM livro
JOIN editora ON livro.editora = editora.id_editora
JOIN autor ON livro.autor =  autor.id_autor
JOIN assunto ON livro.assunto = assunto.id_assunto
```

#### Passo 7.2: Selecionar todos os livros com o mesmo tema
Para selecionar todos os livros que pertencem ao mesmo assunto, podemos fazer uma consulta utilizando o comando 
'SELECT' com uma condição 'WHERE' especificando o que quer visualizar

```SQL
SELECT  livro.titulo AS nome, 
        assunto.descricao_assunto AS assunto
FROM livro
JOIN assunto ON livro.assunto = assunto.id_assunto
WHERE assunto.id_assunto = 5
```









