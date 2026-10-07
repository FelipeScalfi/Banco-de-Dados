## Para a Contagem de Linhas:
```sql
SELECT COUNT(*) FROM produtos;
```
---
## Apelidando a contagem:
```sql
SELECT COUNT(*) AS total_registros
FROM produtos;
```
---
## Selecionando produtos, com determinado estoque:
```sql
SELECT COUNT(*) AS produtos_baixo_estoque
FROM produtos
WHERE estoque >= 10;
```
---
## Contando produtos de uma determinada categoria:
```sql
SELECT COUNT(*) AS total_perifericos
FROM produtos
WHERE categoria = 'Notebooks';
```

## Caso você queira saber o nome do produto mais caro:
```sql
SELECT NOME, preco
FROM produtos
ORDER BY preco DESC;
```

## Para obter a media:
```sql
SELECT AVG(preco) AS media_preco
FROM produtos;
```

## Média arredondada:
```sql
SELECT ROUND(AVG(preco))
 AS media_preco
FROM produtos;
```

## Para exibir tudo em uma consulta:
```sql
SELECT 
MAX (preco) AS preco_maximo,
MIN (preco) AS preco_minimo,
ROUND(AVG(preco), 2) AS media,
SUM(estoque) AS total_produtos
FROM produtos;
```

## Para somar o total de faturamento, vendendo todos os produtos da terabyte:
```sql
SELECT SUM(preco*estoque) AS total_faturamento
FROM produtos;
```
