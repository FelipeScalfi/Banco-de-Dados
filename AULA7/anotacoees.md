## Para contagem de linhas
```SQL
SELECT COUNT(*)
FROM produtos;
```

## Para nomear uma tabela como se fosse um apelido (AS):
```SQL
SELECT COUNT(*) AS total_de_produtos FROM produtos;
```
## Separar valores
```SQL
SELECT MAX(preco) AS produto_mais_caro,
 MIN(preco) AS produto_mais_barato
FROM produtos;
```
## Média/ Média arredondada
```SQL
SELECT AVG(preco) FROM produtos;
```

```SQL
SELECT ROUND(AVG(preco), 2) AS media_preco
FROM produtos;
```

## Soma
```SQL
SELECT SUM(estoque) AS total_de_ptodutos
FROM produtos;
```
---

>Nesse exemplo ele ira separar, somar fazer a média e arredondar os valores:
```SQL
SELECT COUNT(*) AS total_de_ptodutos,
MIN(preco) AS preco_minimo,
MAX(preco) AS preco_maximo,
ROUND(AVG(preco), 2) AS preco_medio,
SUM(estoque) AS total_estoque
FROM produtos;
```
---
```SQL
SELECT nome,preco,estoque,
preco*estoque AS total_estoque
FROM produtos
ORDER BY total_estoque DESC;
```