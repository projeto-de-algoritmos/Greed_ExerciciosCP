# Sumário

- [Sumário](#sumário)
- [Positive Array](#positive-array)
  - [Entrada](#entrada)
  - [Saída](#saída)
  - [Restrições](#restrições)
  - [Exemplos](#exemplos)
    - [Entrada 1](#entrada-1)
    - [Saída 1](#saída-1)
- [Solução](#solução)

# [Positive Array](https://www.codechef.com/problems/CIREQ)

​A 1-indexed array is called positive if every element of the array is greater than or equal to the index on which it lies. Formally, an array **B** of size **M** is called positive if **B<sub>i</sub>** ≥ **i** for each 1 ≤ **i** ≤ **M**.

For example, the arrays [1],[2,2],[3,2,4,4] are positive while the arrays [2,1],[3,1,2] are not positive.

You are given an array **A** containing **N** integers. You want to distribute all elements of the array into some positive arrays. The elements of a positive array might not occur in the order they appear in the array **A**.

Find the minimum number of positive arrays that the elements of the array **A** can be divided into.

Please see the sample cases below for more clarity.

## Entrada

- The first line of input will contain a single integer **T**, denoting the number of test cases.
- Each test case consists of two lines of input.
  - The first line of each test case contains an integer **N** — the number of elements in the array **A**.
  - The next line contains **N** space-separated integers **A<sub>1</sub>**,**A<sub>2</sub>**,…,**A<sub>N</sub>** — the elements of array **A**.

## Saída

For each test case, output on a new line the minimum number of positive arrays that the elements of the array **A** can be divided into.

## Restrições

- 1 ≤ **T** ≤ 10<sup>4</sup>
- 1 ≤ **N** ≤ 10<sup>5</sup>
- 1 ≤ **A<sub>i</sub>** ≤ **N**
- The sum of **N** over all test cases won't exceed 2⋅10<sup>5</sup>

## Exemplos

### Entrada 1

```
5
3
2 3 3
4
3 1 1 2
3
1 1 1
5
1 2 2 4 5
6
3 2 1 2 2 1
```

### Saída 1
```
1
2
3
2
3
```

# [Solução](./solution.cpp)

É possível mostrar que sempre que um array é considerado um _Array Positivo_, se ordenarmos-o de forma não decrescente ele continuará sendo um _Array Positivo_.

Para resolver o problema, criamos um container inicialmente vazio `S` que guardará o índice atual (quantidade de elementos + 1) de todos os _Array Positivo_ que temos até o momento. Então processamos a entrada em ordem não decrescente, para cada elemento do array **A** procuramos um _Array Positivo_ em `S` com o maior índice menor ou igual ao valor que estamos processando **A<sub>i</sub>** (Utilizando uma estrutura ordenada, essa busca fica O(log(|`S`|))). Caso encontremos um _Array Positivo_ com essa propriedade incrementamos o índice desse _Array Positivo_, caso contrário criamos um novo _Array Positivo_ em `S` com o índice **2** (já que a primeira posição será ocupada pelo elemento que está sendo processado).

Note que graças às propriedades do problema o container utilizado para `S` pode ser um vetor em ordem não crescente, visto que sempre será adicionado o menor valor possível **2** no final, e caso seja implementado o algoritmo descrito acima, sua ordenação será preservada durante todas as operações.
