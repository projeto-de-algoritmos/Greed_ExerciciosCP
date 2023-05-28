# Sumário

- [Sumário](#sumário)
- [The Lazy Programmer](#the-lazy-programmer)
  - [Entrada](#entrada)
  - [Saída](#saída)
  - [Exemplos](#exemplos)
    - [Entrada 1](#entrada-1)
    - [Saída 1](#saída-1)
- [Solução](#solução)

# [The Lazy Programmer](https://www.spoj.com/problems/LAZYPROG/en/)

A new web-design studio, called SMART (Simply Masters of ART), employs two people. The first one is a web-designer and an executive director at the same time. The second one is a programmer. The director is so a nimble guy that the studio has already got **N** contracts for web site development. Each contract has a deadline **d<sub>i</sub>**.

It is known that the programmer is lazy. Usually he does not work as fast as he could. Therefore, under normal conditions the programmer needs **b<sub>i</sub>** of time to perform the contract number **i**. Fortunately, the guy is very greedy for money. If the director pays him **x<sub>i</sub>** dollars extra, he needs only **(b<sub>i</sub> - a<sub>i</sub>*x<sub>i</sub>)** of time to do his job. But this extra payment does not influence other contracts. This means that each contract should be paid separately to be done faster. The programmer is so greedy that he can do his job almost instantly if the extra payment is **(b<sub>i</sub>/a<sub>i</sub>)** dollars for the contract number **i**.

The director has a difficult problem to solve. He needs to organize programmer’s job and, may be, assign extra payments for some of the contracts so that all contracts are performed in time. Obviously he wishes to minimize the sum of extra payments. Help the director!

## Entrada

First line of the input contains an integer **t** (1 ≤ **t** ≤ 45), equal to the number of testcases. Then descriptions of **t** testcases follow.

First line of description contains the number of contracts **N** (1 ≤ **N** ≤ 100000, integer). Each of the next **N** lines describes one contract and contains integer numbers **a<sub>i</sub>, b<sub>i</sub>, d<sub>i</sub>** (1 ≤ **a<sub>i</sub>, b<sub>i</sub>** ≤ 10000; 1 ≤ **d<sub>i</sub>** ≤ 1000000000) separated by spaces.

At least 90% of testcases will have 1 ≤ **N** ≤ 10000.

## Saída

For each testcase in the input your program should output one line with a single real number **S**. Here **S** is the minimum sum of money which the director needs to pay extra so that the programmer could perform all contracts in time. The number must have two digits after the decimal point.

## Exemplos

### Entrada 1

```
1
2
20 50 100
10 100 50
```

### Saída 1
```
5.00
```

# [Solução](./solution.cpp)

Assim como no problema Minimizing Lateness, neste problema também devemos processar a entrada ordenadas de forma não decrescente pela deadline.

Podemos armazenar uma variável para dizer em qual dia nós estamos `day`, e outra para guardar o dinheiro total gasto até o momento `money`, ambas inicializadas em 0. Para cada tarefa incrementamos o dia pela quantidade de dias que o programador precisa para concluí-la **b** e adicionamos essa tarefa em uma fila de prioridades onde a chave é o valor **a** (o quão mais rápido o programador realiza a atividade caso receba um dinheiro extra). Com isso, sempre que `day` for maior que a deadline da tarefa atual teremos que pagar mais para a tarefa que esteja no topo da fila, visto que ela é a tarefa que o diretor recebe maior benefício por dollar gasto. A quantidade de dinheiro gasto pelo diretor nesta tarefa desse ser apenas o suficiente para que ela seja cumprida até o dia atual `day`. No caso em que mesmo concluindo a tarefa instantaneamente ela ainda atrase, o diretor deve pagar o suficiente para concluí-la imediatamente e passar para a próxima tarefa até que elas sejam cumpridas dentro do prazo. Em cada operação os valores `money` e `day` devem ser atualizados de acordo.
