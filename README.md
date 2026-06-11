# Sistema de Manutenção de Contas

## Descrição

Este programa implementa um sistema simples de manutenção de contas bancárias utilizando arquivos binários em C. Os dados dos clientes são armazenados em registros de tamanho fixo, permitindo acesso direto a qualquer posição do arquivo.

## Estrutura do Registro

Cada cliente é representado pela estrutura:

```c
typedef struct {
    int numeroConta;
    char nome[50];
    float saldo;
    int ativo;
} Cliente;
```

O campo `ativo` é utilizado para indicar se a conta está ativa (`1`) ou encerrada (`0`).

## Funcionalidades

O sistema possui as seguintes opções:

1. Cadastrar um novo cliente em uma posição específica.
2. Consultar um cliente pelo número da conta.
3. Atualizar o saldo de um cliente.
4. Encerrar uma conta.
5. Listar todos os clientes ativos.
6. Reposicionar a leitura para o início do arquivo.
7. Encerrar o programa.

## Manipulação do Arquivo

O programa utiliza o arquivo binário `clientes.dat` para armazenar os registros.

### Escrita e Leitura

A gravação dos registros é realizada com:

```c
fwrite()
```

A leitura dos registros é realizada com:

```c
fread()
```

### Acesso Direto aos Registros

Para acessar uma posição específica do arquivo é utilizada a função:

```c
fseek()
```

O deslocamento é calculado multiplicando a posição desejada pelo tamanho da estrutura:

```c
fseek(arquivo, posicao * sizeof(Cliente), SEEK_SET);
```

### Reinício da Leitura

Para reposicionar o ponteiro do arquivo no início é utilizada a função:

```c
rewind()
```

Essa funcionalidade permite repetir leituras e listagens sem fechar e reabrir o arquivo.

## Remoção de Clientes

Os registros não são removidos fisicamente do arquivo. Ao encerrar uma conta, o campo `ativo` recebe o valor `0`, caracterizando uma remoção lógica.

## Conclusão

A solução atende aos requisitos do exercício utilizando:

- Arquivo binário.
- Registros de tamanho fixo.
- `fseek()` para acesso direto.
- `fread()` para leitura.
- `fwrite()` para gravação.
- `rewind()` para reposicionar a leitura.
- Remoção lógica de registros.
