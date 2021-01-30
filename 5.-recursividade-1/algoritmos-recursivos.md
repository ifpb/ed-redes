# Visão geral

## Recursividade

Um algoritmo é denominado recursivo quando sua definição é parcialmente feita em termos dele mesmo. A idéia básica de um algoritmo recursivo consiste em **diminuir sucessivamente o problema** em um **problema menor** ou mais simples, até que o tamanho permita resolvê-lo de forma direta, sem recorrer a si mesmo. Quando isso ocorre, diz-se que o algoritmo atingiu uma **condição de parada**, a qual deve estar presente em pelo menos um local dentro algoritmo. Sem esta condição o algoritmo não irá parar de chamar a si mesmo, até estourar a capacidade da pilha, o que geralmente causa efeitos colaterais e até mesmo o término indesejável do programa.

Para cada chamada de uma função, os parâmetros e as variáveis locais são movidas para uma pilha de execução. Internamente, quando qualquer chamada de função é feita dentro de um programa, é criado um registro de ativação nessa pilha. O registro de ativação armazena os parâmetros e variáveis locais da função, bem como o “ponto de retorno” no programa ou subprograma que chamou esta função. Ao final da execução, o registro é desempilhado e a execução volta ao subprograma que chamou a função.

O tempo de execução é maior do que chamadas múltiplas dentro de um laço, por exemplo, devido ao _overhead_ introduzido pelo gerenciamento das chamadas recursivas na pilha de execução.

**Exemplo 1:** vamos fazer um algoritmo que imprima recursivamente todos os primeiros cinco números inteiros.

```text
def imprimir_numero_recursivo(num: int):
  if num < 5:
    print(num)
    imprimir_numero_recursivo(num + 1)
```

Resultado:

```text
0
1
2
3
4
```

Note que o método `imprimir_numero_recursivo`chama a si mesmo em parte da execução. A condição de parada neste caso é `num < 5` . Ou seja, a função for chamada com o parâmetro 5, o programa irá concluir a execução. 

![Ilustra&#xE7;&#xE3;o da Pilha de Execu&#xE7;&#xE3;o do Exemplo 1](https://documents.app.lucidchart.com/documents/a4b39668-f3eb-4654-8a2b-b75e5ba2fd43/pages/0_0?a=206&x=18&y=135&w=924&h=550&store=1&accept=image%2F*&auth=LCA%20ad8c9d71b2223c68270ca1586790682983c8611b-ts%3D1601070739)

**Exemplo 2:** vamos imprimir recursivamente todos os primeiros cinco números inteiros, porém, em outra versão.

```text
def imprimir_numero_recursivo2(num: int):
  if num < 5:
    imprimir_numero_recursivo2(num + 1)
    print(num)

imprimir_numero_recursivo2(0)
```

Resultado:

```text
4
3
2
1
0
```

![Ilustra&#xE7;&#xE3;o da Pilha de Execu&#xE7;&#xE3;o do Exemplo 2](https://documents.app.lucidchart.com/documents/a4b39668-f3eb-4654-8a2b-b75e5ba2fd43/pages/0_0?a=335&x=918&y=134&w=924&h=577&store=1&accept=image%2F*&auth=LCA%204aa69a28466d5dfff2202efcd9b05d318aa0470a-ts%3D1601072495)

Note que como a chamada recursiva ocorre antes do comando print, os elementos agora são impressos em ordem decrescente.

**Exemplo 3:** somar todos os números inteiros entre `m` e `n`

```text
def soma(m: int, n: int) -> int:
  if m == n:
    return m
  else:
    return m+soma(m+1, n)

soma(1,5)
```

**Resultado:** 15

![&#xC1;rvore de recurs&#xE3;o para o exemplo 3](../.gitbook/assets/screen-shot-2020-09-26-at-19.29.53%20%281%29.png)

### Recursão em Cauda VS Recursão Crescente

**Recursão Crescente** ⇨ Depois de encerrada a chamada recursiva, outras operações ainda são realizadas.

**Recursão em Cauda** ⇨ Não existe processamento a ser realizado depois de encerrada a chamada recursiva, ou seja, a chamada recursiva é a última instrução a ser executada. 

A recursão em cauda geralmente é mais rápida do que recursão crescente, uma vez que não é necessário armazenar todo o contexto na pilha de execução do programa. Os exemplos 1 e 3 contêm recursões em cauda, enquanto o exemplo 2 ilustra uma recursão crescente.

### Considerações

* Todo algoritmo recursivo possui uma versão iterativa equivalente, bastando utilizar uma pilha explícita \(utilizando laços de repetição\);
* Usualmente, os compiladores transformam automaticamente funções recursivas de código em funções iterativas;
* Quando se trata de recursividade em cauda, ela é utilizada com maior facilidade;
* Algumas linguagens funcionais não possuem laços de repetição, apenas recursividade
* É necessário estar atento ao fator de ramificação da recursão, ou seja, quantas chamadas recursivas serão feitas por vez
* Caso haja erros de implementação, há chance de loop infinito ou estouro da pilha de execução

### Algoritmos Recursivos Vs Iterativos

A sucessão de **Fibonacci** é uma sequência de números inteiros iniciados por zero e um, no qual cada termo subsequente corresponde a soma dos dois números anteriores: 0,1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987, 1597...

Abaixo um exemplo da implementação desse algoritmo de maneira recursiva e de maneira iterativa.

Fibonacci Recursivo

```text
def fib_rec(n: int) -> int:
  if n <= 1:
    return n
  else:
    return fib_rec(n-1) + fib_rec(n-2)

print(fib_rec(5))
```

Fibonacci Iterativo

```text
def fib_ite(n: int) -> int:
  i: int = 1
  fib: int = 1
  anterior: int = 0
  while i < n:
    temp = fib
    fib = fib + anterior
    anterior = temp
    i += 1
  return fib

print(fib_ite(5))
```

[Veja aqui](exemplos/detalhes-algoritmo-de-fibonacci-recursivo.md) a descrição detalhada de cada etapa executada pelo algoritmo Fibonacci recursivo.

Note que a versão recursiva apresentará problema ao testar valores grandes, como por exemplo, 40, 50. Para aprimorar a versão recursiva do Fibonacci seria necessário utilizar um vetor para armazenar os valores já calculados \(passando-o como um dos parâmetros da função, evitando o recalculo.

Logo, o algoritmo proposto é extremamente ineficiente, pois recalcula repetidas vezes o mesmo valor. A complexidade de tempo para calcular o resultado, considerando as operações de adição, é O\(o\(n\)\), enquanto que a versão iterativa deste algoritmo possui complexidade de tempo O\(n\). Veja abaixo uma comparação do desempenho das duas abordagens:

| n | 20 | 30 | 50 | 100 |
| :--- | :--- | :--- | :--- | :--- |
| Recursivo | 1s | 2m | 21 dias | 10^9 anos |
| Iterativo | 1/3 ms | 1/2 ms | 3/4 ms | 1,5 /ms |

### Considerações

A recursividade é uma técnica natural para expressar algoritmos definidos em termos de recorrências. Estes algoritmos são geralmente traduções de equações de recorrência em uma determinada linguagem de programação. 

Deve ser analisada a eficiência dos algoritmos recursivos, principalmente o fator de ramificação e o crescimento da pilha de execução. Em boa parte dos casos, a recursividade pura é utilizada mais como técnica conceitual do que como técnica computacional.



