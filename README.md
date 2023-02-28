# 🎥 Trabalho prático A3
## Otimização de consultas

📆 **Data de entrega**: 14/02/2020

📝 **Descrição**: Um cliente deseja melhorar o desempenho do seu banco de dados. Para isto, você foi acionado para verificar o que está ocorrendo com o banco de dados. Nesse contexto, sua tarefa é criar consultas e verificar como o SGBD a está implementando. A tarefa será apresentada para o cliente (e a turma ;))

**Banco de dados**: será utilizado o banco disponível neste link https://github.com/credativ/omdb-postgresql

**Tarefa 1**  
Carregar o dataset no SGBD Postgres.

**Tarefa 2**  
Criar duas consultas com joins sobre as tabelas com os maiores número de tuplas;

**Tarefa 3**  
Comparar e reportar o **custo de execução** com e sem índice (usar o comando explain*). A consulta está utilizando o índice? Executar a consulta 5 vezes e calcular a média e o desvio. Explicar o plano da consulta.
Atentar: Qual algoritmo foi usado para realizar o Join? Explique o seu funcionamento.

## Como carregar o banco de dados
Primeiro, é necessário clonar o repositório do github.

```bash
git clone https://github.com/credativ/omdb-postgresql
```

Caso seu nome de usuário do postgres seja diferente do usuário do sistema, é necessário criar. Para isso, basta executar o comando abaixo.

```bash
sudo -u postgres createuser -s $USER
```

Em seguida, seguindo as instruções do repositório, é necessário criar o banco de dados e carregar os dados.

```bash
cd omdb-postgresql	
./download
./import
```

Para acessar o banco de dados, basta executar o comando abaixo.

```bash
sudo -u postgres psql
\c omdb
```
## Análise de desempenho
Para analisar o desempenho das consultas, foi utilizado o comando `EXPLAIN` do Postgres. O comando `EXPLAIN` retorna o plano de execução da consulta, que é composto por uma árvore de operações. Cada nó da árvore representa uma operação que será realizada para executar a consulta. O comando `EXPLAIN` também retorna o custo estimado de cada operação e o custo total da consulta.

Todos os cálculos foram realizados utilizando o comando `EXPLAIN ANALYZE`, que além de retornar o plano de execução, também executa a consulta e retorna o tempo de execução.

Os cálculos podem ser encontrados também [nesta planilha](https://docs.google.com/spreadsheets/d/1-Kdt59DL8dX9xvrQSFzTBdK3uidualAdOoZVBnuLlVA/)

## Consulta 1:

### Sem índice:

**Tempos de execução:**

**Cálculo da Média**  

**Cálculo do Desvio Padrão**  

### Com índice:

**Tempos de execução:**


**Cálculo da Média**


**Cálculo do Desvio Padrão**

## Consulta 2

### Sem índice:

**Tempos de execução:**

**Cálculo da Média**

**Cálculo do Desvio Padrão**

### Com índice:

**Tempos de execução:**

**Cálculo da Média**

**Cálculo do Desvio Padrão**


# Conclusão

Utilizando os conceitos de otimização de consultas, foi possível identificar os principais gargalos de desempenho de uma consulta e otimizá-la. Além disso, foi possível identificar os tipos de junções mais adequados para cada situação e criar índices para melhorar o desempenho de consultas semelhantes.
