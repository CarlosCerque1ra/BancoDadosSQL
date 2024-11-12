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

```
CREATE DATABASE biblioteca;
USE biblioteca;
```

### 1.2 Criando a tabela 'editora'
```
CREATE TABLE editora(
    id_editora INT PRIMARY KEY  AUTO_INCREMENT,
    nome_editora VARCHAR(100) NOT NULL,
    pais VARCHAR(50)
);
```

#### 1.3 Criando a tabela 'autor'
```
CREATE TABLE autor(
    id_autor INT PRIMARY KEY  AUTO_INCREMENT,
    nome_autor VARCHAR(200),
    data_nascimento DATE
);
```

#### 1.4 Criando atabela 'assunto'
```
CREATE TABLE assunto(
    id_assunto INT PRIMARY KEY  AUTO_INCREMENT,
    descricaio_assunto VARCHAR(500) NOT NULL,
);
```

#### 1.5 Crindo a tabela 'livro'
```
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

```
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
('Jorge Amado', '1912-08-10', 'jorginho@gmail.com')
('Machado de Assis', '1839-06-21', 'machadinho@gmail.com')
('Matt Haig', '1975-06-03', 'matt@gmail.com')
```

#### 4.3 Inserindo dados na tabela 'assunto'
```SQL
INSERT INTO assunto (descricao_assunto)
VALUES
('Ficção')
('Mistério')
('Terror')
('Ação')

```




