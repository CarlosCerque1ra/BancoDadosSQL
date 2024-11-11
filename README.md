# BancoDadosSQL

# Passo a passo: Criação de um banco de dados
Tutoria de como criar um banco de dados SQL que organiza as informações de 'livros', 'editora', 'autores' e 'assuntos'.
Este guia será dividido em etapas para demonstrar desde a criação de tabelas, chave e até manipulação/consulta de dados.
## Resumo da estrutura SQL
*__CREATE__ para criar 'Banco de dados' ou 'Tabelas'
*__ALTER__ para adicionar ou modificar colunas
*__DROP__ para remover 'Banco de dados' ou 'Tabelas'
*__INSERT__ para adicionar registros na tabela
*__UPDATE__ para atualizar os registros
*__PARA__ para remover os registros
*__SELECT__ para consultar e visualizar dados

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
    descricap_assunto VARCHAR(300) NOT NULL,
    data_nascimento DATE
);
```

####