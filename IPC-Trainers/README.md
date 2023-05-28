# Sumário

- [Sumário](#sumário)
- [IPC Trainers](#ipc-trainers)
  - [Entrada](#entrada)
  - [Saída](#saída)
  - [Restrições](#restrições)
  - [Exemplos](#exemplos)
    - [Entrada 1](#entrada-1)
    - [Saída 1](#saída-1)
- [Solução](#solução)

# [IPC Trainers](https://www.codechef.com/problems/IPCTRAIN)

During the Indian Programming Camp (IPC), there are **N** trainers. The camp runs for **D** days. Each day, there can be at most one lecture. The i-th trainer arrives on day **D<sub>i</sub>** and then stays till the end of the camp. He also wants to teach exactly **T<sub>i</sub>** lectures. For each lecture that a trainer was not able to teach, he will feel sad and his sadness level will be increased by **S<sub>i</sub>**.

You are the main organizer of the contest. You want to find minimum total sadness of the trainers.

## Entrada

The first line of the input contains an integer **T**, denoting the number of testcases.

For each test case, the first line contains two space separated integers, **N**, **D**.

The i-th of the next **N** lines will contain three space separated integers: **D<sub>i</sub>**, **T<sub>i</sub>**, **S<sub>i</sub>** respectively.

## Saída

For each test case, output a single integer corresponding to the minimum total sadness of the trainers achievable.

## Restrições

- 1 ≤ **T** ≤ 10
- 1 ≤ **N, D** ≤ 10<sup>5</sup>
- 1 ≤ **D<sub>i</sub>, T<sub>i</sub>** ≤ **D**
- 1 ≤ **S<sub>i</sub>** ≤ 10<sup>5</sup>

## Exemplos

### Entrada 1

```
3
2 3
1 2 300
2 2 100
2 3
1 1 100
2 2 300
2 3
3 2 150
1 1 200
```

### Saída 1
```
100
0
150
```

# [Solução](./solution.cpp)

Como apenas um treinador pode palestrar por dia, a melhor estratégia para cada dia deixar que o treinador com maior nível de tristeza e que ainda queira palestrar, palestre.

Para isso, podemos ir processando um dia por vez e guardar os treinadores que já chegaram e ainda querem palestrar em uma fila de prioridades tendo como chave o nível de tristeza de cada um. Em cada dia que a fila de prioridades não esteja vazia, retiramos o treinador do topo e deixamos que ele palestre naquele dia, reduzindo assim a quantidade de dias que esse treinador quer palestrar em 1 unidade.

Por fim, iteramos por cada treinador pendente da fila de prioridades que não conseguiram palestrar o quanto desejavam e somamos na resposta o nível de tristeza multiplicado pela quantidade de dias que não conseguiram palestrar.
