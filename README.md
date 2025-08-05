# ___Explorando-Bancos-de-Dados___
---
## ___Banco de Dados___
```Definição:``` Coleção organizada e armazenada de informações de modo que seja mais fácil acessar e gerenciar.

Este conceito pode ser destrinchado em 2 estados:
- _Relacional_
- _Não relacional_

![]()

---

### ___Banco de Dados Relacional___

Um banco de dados relacional é um tipo de banco de dados que armazena e fornece acesso a pontos de dados relacionados entre si. Basicamente, são baseados no modelo de relação, uma maneira intuitiva e direta de representar dados em tabelas, com linhas e colunas separadas com IDs exclusivos facilitando o estabelecimento das relações entre os pontos.

#### __Exemplo de Uso:__ ###

Uma farmacia que relaciona os dados de estoque. Resumidamente, usa chaves estrangeiras para chegar em uma chave primaria (ID exclusivo), o remédio sendo encontrado em através de colunas e linhas da tabela com informações sobre produto e sua quantidade.

---

### ___Banco de Dados Não Relacional___

Um banco de dados não relacional é um banco de dados que não usa o esquema de tabela de linhas e colunas. Em contra partida, eles utilizam um modelo de armazenamento otimizado para os requisitos específicos do tipo de dados que está sendo armazenado, com altas taxas de atualização, como graficos ou documentos JSON.

#### __Exemplo de Uso:__ ###

Uma plataforma de streaming que necessita saber as prefências dos usuários. Para este fim é necessário que os dados estejam ordenados em um gráfico que mostre as preferências e suporte uma atualização constante de dados.

---

## ___Processo de Normalização___

A normalização de dados é um processo que organiza as informações em um banco de dados para reduzir a redundancia e melhorar a integridade dos dados. Basicamente, ela visa eliminar informação duplicado e inconsistente, facilitando a manipulação e análise das informações.

### ___Normalizando:___

```Tabela não normalizada```

|Pedido_ID|Cliente_Nome|Cliente_Endereço|Produto_ID|Quantidade|Preço_Total|
|---------|------------|----------------|----------|----------|-----------|
  |1|     João Silva    |   Rua A, 123         |   10             | Caneta          |   2       |   4,00         |
  |1|     João Silva    |   Rua A, 123         |   11             | Lápis           |   1       |   2,00         |
  |2|     Maria Souza   |   Av. B, 456         |   10             | Caneta          |   5       |  10,00         |

  ---


```1ª Forma Normal```
Criando uma tabela de clientes, extraimos os: Cliente_ID, Nome e Endereço.

| Cliente_ID | Nome        | Endereço  |
|------------|-------------|-----------|
| 1          | João Silva  | Rua A, 23 |
| 2          | Maria Souza | Av. B,456 |
- Retiramos as repetições
---

```2ª Forma Normal```
Criando uma tabela de produtos, extraimos os: Produto_ID, Produto_Nome.
| Produto_ID| Produto_Nome |
|-------------|-----------|
|10  | Caneta |
|11  | Lápis  |
- Retiramos as dependencias parciais
---
```3ª Forma Normal```
Criando uma tabela de itens, extraimos os: Produto_ID, Pedido_ID, Quantidade, Preço_Total.
| Pedido_ID | Produto_ID | Quantidade | Preço_Total |
|-----------|------------|------------|-------------|
| 1         | 10         | 2          | 4,00        |
| 1         | 11         | 1          | 2,00        |
| 2         | 10         | 5          | 10,00       |
- Retiramos as dependencias transitivas
---
## ___Estrutura Não Relacional(MongoDB)___

Este tipo de estrutura é devidamente utilizado devido a flexibilidade, velocidade e escalabilidade. A falta da necessidade de criação de tabelas acelera e otimiza os dados, abrindo possibilidades para mais dados, e, consequentemente Big Data, onde a manipulação humana ficaria invíavel.


```json

  {
    "pedido_id": 1,
    "cliente": {
      "cliente_id": 1,
      "nome": "João Silva",
      "endereco": "Rua A, 123"
    },
    "itens": [
      {
        "produto_id": 10,
        "produto_nome": "Caneta",
        "quantidade": 2,
        "preco_total": 4.00
      },
      {
        "produto_id": 11,
        "produto_nome": "Lápis",
        "quantidade": 1,
        "preco_total": 2.00
      }
    ]
  },
  {
    "pedido_id": 2,
    "cliente": {
      "cliente_id": 2,
      "nome": "Maria Souza",
      "endereco": "Av. B, 456"
    },
    "itens": [
      {
        "produto_id": 10,
        "produto_nome": "Caneta",
        "quantidade": 5,
        "preco_total": 10.00
      }
    ]
  }
```







