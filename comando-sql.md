# Comandos SQl - Referências

## Modelagem Física com comandos DDL

### Criar banco de dados

CREATE DATABASE vendas CHARACTER SET utf8mb4;

### Criar tabela de fabricantes

```sql
CREATE TABLE fabricantes(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL
);
```

### Visualizar detalhes estruturais da tabela

```sql
DESC fabricantes;
```


### Criar tabela de produtos

```sql
CREATE TABLE produtos(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    descricao TEXT(500),
    preco DECIMAL(6,2),
    fabricante_id INT NOT NULL
);
```

### Visualizar detalhes estruturais da tabela

```sql
DESC produtos;
```

### Criação do relacionamento entre as tabelas (chave estrangeira)

``` sql
ALTER TABLE produtos
    -- CONSTRAINT/RESTRIÇÃO indicando o nome do relacionamento
    ADD CONSTRAINT fk_produtos_fabricantes

    -- Criando a chave-estrangeira (fabricante_id) que
    -- aponta para a chave-primária (id) de outra tabela (fabricantes)
    FOREIGN KEY (fabricante_id) REFERENCES fabricantes(id)
```

### Exemplos de alteração de estrutura na tabela

#### Renomear tabela

```sql
ALTER TABLE fabricantes RENAME TO fornecedores;
ALTER TABLE  fornecedores RENAME TO  fabricantes;
```


#### Modificar Colunas

```sql
ALTER TABLE produtos
    MODIFY COLUNM preco INT NOT NULL;

```

#### Renomear Colunas

```sql
ALTER TABLE fabricantes
    CHANGE nome sobrenome VARCHAR(20) NOT NULL;
```

#### Adicionar Colunas

```sql
ALTER TABLE produtos
    ADD quantidade INT NULL AFTER preco;
```