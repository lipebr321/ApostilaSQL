# 🎓 Tutorial Completo: Criação de Bancos e Tabelas em SQL

Bem-vindo ao guia definitivo para criar bancos de dados e tabelas em SQL! Este tutorial apresenta exemplos práticos e detalhados para você entender como estruturar e implementar diferentes tipos de bancos de dados.

---

## 📂 O que é um Banco de Dados?

Um banco de dados é uma coleção organizada de informações que podem ser facilmente acessadas, gerenciadas e atualizadas. Em SQL, criamos e manipulamos bancos de dados com comandos específicos.

---

## 🛠️ Passos para Criar um Banco de Dados

### 1. Criar um Banco de Dados
```sql
CREATE DATABASE MeuBancoDeDados;
CREATE DATABASE: Comando para criar um banco de dados.
MeuBancoDeDados: Nome do banco de dados. Escolha um nome descritivo.
```
---

2. Selecionar o Banco de Dados para Uso
   
```sql

USE MeuBancoDeDados;
Isso define qual banco de dados será usado para as operações subsequentes.
```

📝 Exemplos de Criação de Bancos de Dados
Banco de Dados para Gerenciamento de Loja

```sql

CREATE DATABASE LojaVirtual;
USE LojaVirtual;
Banco de Dados para Controle Acadêmico

```
```sql
CREATE DATABASE SistemaAcademico;
USE SistemaAcademico;
Banco de Dados para Redes Sociais
```
```sql
CREATE DATABASE RedeSocial;
USE RedeSocial;
```
🏗️ Criação de Tabelas
1. Estrutura Básica de uma Tabela
   
```sql
CREATE TABLE NomeDaTabela (
    NomeColuna TipoDados Restricoes
);
NomeDaTabela: Nome da tabela.
NomeColuna: Nome de cada coluna.
TipoDados: Tipo de dado que a coluna armazena (ex.: INT, VARCHAR, DATE).
Restricoes: Regras opcionais (ex.: PRIMARY KEY, NOT NULL).

```
📋 Exemplos Práticos de Criação de Tabelas
Tabela para Loja Virtual: Produtos


```sql
CREATE TABLE Produtos (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    Nome VARCHAR(100) NOT NULL,
    Preco DECIMAL(10, 2) NOT NULL,
    Estoque INT DEFAULT 0,
    Categoria VARCHAR(50),
    DataCadastro DATE DEFAULT CURRENT_DATE
);

```

AUTO_INCREMENT: Incrementa automaticamente o ID.
DEFAULT: Define um valor padrão, como 0 para estoque.
Tabela para Sistema Acadêmico: Alunos


```sql
CREATE TABLE Alunos (
    Matricula INT PRIMARY KEY,
    NomeCompleto VARCHAR(100) NOT NULL,
    DataNascimento DATE NOT NULL,
    Curso VARCHAR(50),
    Periodo INT CHECK (Periodo BETWEEN 1 AND 10)
);
```
CHECK: Define uma restrição, como o intervalo de períodos.
Tabela para Rede Social: Usuários

```sql
CREATE TABLE Usuarios (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    Nome VARCHAR(50) NOT NULL,
    Email VARCHAR(100) UNIQUE NOT NULL,
    Senha VARCHAR(255) NOT NULL,
    DataCriacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

```

UNIQUE: Garante que os valores de uma coluna sejam únicos.
🔗 Relacionamentos entre Tabelas
Tabela de Pedidos Relacionada a Produtos e Clientes

```sql
CREATE TABLE Clientes (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    Nome VARCHAR(100),
    Email VARCHAR(100) UNIQUE
);
```
```sql

CREATE TABLE Pedidos (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    ClienteID INT,
    ProdutoID INT,
    Quantidade INT NOT NULL,
    DataPedido TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (ClienteID) REFERENCES Clientes(ID),
    FOREIGN KEY (ProdutoID) REFERENCES Produtos(ID)
);
```
FOREIGN KEY: Estabelece relações entre tabelas.
🌟 Dicas Avançadas
Índices para Otimização de Consultas

```sql
CREATE INDEX idx_nome ON Produtos (Nome);
```

Índices ajudam a acelerar consultas, especialmente em colunas frequentemente pesquisadas.
Tabelas com Chave Composta

```sql
CREATE TABLE Matriculas (
    AlunoID INT,
    CursoID INT,
    DataMatricula DATE,
    PRIMARY KEY (AlunoID, CursoID)
);
```
Combina duas colunas para formar uma chave primária.


🧩 Exercícios Práticos
Crie um banco de dados chamado Biblioteca com tabelas para Livros, Autores e Emprestimos.
Relacione as tabelas de forma que um autor possa ter vários livros e um livro possa ser emprestado para vários leitores.
Adicione restrições como NOT NULL, DEFAULT e FOREIGN KEY para enriquecer as tabelas.

🚀 Conclusão
Criar bancos de dados e tabelas em SQL é uma habilidade essencial para gerenciar informações de forma eficiente. Este tutorial cobriu desde conceitos básicos até exemplos práticos e avançados. Continue praticando para dominar o SQL!

Feito com 💙 por Luis Felipe Pereira.
