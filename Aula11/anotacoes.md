## Relacionamentos entre tabelas

- Ideia principal: Um cliente pode possuir vários pedidos.

## Diagrama

```mermaid
erDiagram
CLIENTES ||--o{PEDIDOS : faz

CLIENTES{
    id int PK
    nome VARCHAR(50)
}

PEDIDOS{
    id int PK
    produto varchar(50)
    id_cliente int FK
}
```
1-Primeiro criamos a nossa tabela:
```sql
CREATE TABLE clientes(
    id SERIAL PRIMARY KEY,
    nome VARCHAR(50) NOT NULL
);
```
2-Criamos a tabela pedidos, referenciando com a coluna ID da tabela clientes:
```sql
CREATE TABLE pedidos(
    id SERIAL PRIMARY KEY,
    produto VARCHAR(50) NOT NULL,
    id_cliente INT REFERENCES clientes(id)
);
```
3-Adicionaremos os clientes:
```sql
INSERT INTO clientes (nome) VALUES
('Hannah'),
('Miguel'),
('Murilo'),
('Lucas');
```
4-Veremos os pedidos de cada cliente:
```sql
INSERT INTO pedidos (produto,id_clientes) VALUES
('Chocolate',3),
('salgado',1),
('refri',2),
('Chocolate',3)
```
5-Para verificar quais os produtos cada cliente comprou:
```sql
SELECT clientes.nome,pedidos.produto
FROM pedidos 
INNER JOIN clientes ON pedidos.id_clientes = clientes.id;
```
6- Para verificar todos os clientes, até mesmo os que não compraram nada:
```sql
SELECT clientes.nome,pedidos.produto
FROM clientes
LEFT JOIN pedidos ON pedidos.id_clientes = clientes.id;
```
7- Para aparecer somente o cliente que não fez pedido:
```sql
SELECT clientes.nome,pedidos.produto
FROM clientes
LEFT JOIN pedidos ON pedidos.id_clientes = clientes.id
WHERE pedidos.id IS NULL;
```