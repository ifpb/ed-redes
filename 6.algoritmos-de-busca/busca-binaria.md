# Busca Binária

## Algoritmo de busca binária

O algoritmo de busca binária segue a estratégia de dividir para conquistar. Deve-se encontrar o elemento central da lista e, a partir daí, compará-lo com a chave de pesquisa. Três situações podem ocorrer:

1. O elemento central possui o valor pesquisado, encerra-se o algoritmo;
2. Ele é maior que o valor pesquisado, então, devem-se descartar os elementos à sua esquerda;
3. Ele é menor que o valor pesquisado, logo, devem-se descartar os elementos à sua direita.

Se a chave não foi encontrada, deve-se repetir o processo, com o subconjunto de dados selecionados \(esquerda ou direita\), até encontrá-la ou o subconjunto ser reduzido até se confirmar que o elemento não existe e, neste caso, deve-se encerrar o algoritmo.

Considere o vetor de dados abaixo e a chave de pesquisa **5**. A pesquisa se inicia no elemento central, o qual é encontrado dividindo-se o tamanho do vetor \(considerar a soma dos índices: 0 início e 9 fim\) por 2. O resultado deverá considerar apenas a parte inteira. Neste caso temos: \(0+9\) / 2 = 4,5, usar 4:

![](../.gitbook/assets/image%20%2833%29.png)

Como o valor encontrado é maior que a chave de pesquisa, descartamos a parte direita do vetor e, em seguida, realizamos uma nova divisão. Cálculo do meio: \(0+4\) / 2 = 2:

![](../.gitbook/assets/image%20%2834%29.png)

E, finalmente, encontramos o valor pesquisado.

### Implementação da busca binária

A primeira iteração testa o elemento do meio da lista.

a\) Se ele corresponder à chave de pesquisa, o algoritmo termina.

b\) Se a chave de pesquisa for menor que o elemento do meio, a chave de pesquisa não poderá localizar nenhum elemento na segunda metade da lista e o algoritmo continua apenas na primeira metade.

c\) Se a chave de pesquisa for maior que o elemento do meio, a chave de pesquisa não poderá localizar nenhum elemento na primeira metade do array e o algoritmo continua apenas com a segunda metade do array.

Repare que a cada iteração, metade da lista é descartada, ficando apenas a metade que interessa. E assim sucessivamente até localizar o elemento ou reduzindo o subconjunto ao tamanho zero.

O algoritmo retornará um índice \(posição de um elemento no vetor\) que corresponderá ao valor pesquisado ou um índice com um valor diferente ao pesquisado. 

```text
def busca_binaria(chave: int, vetor: List[int]) -> int:
  primeiro: int = 0
  ultimo: int = len(vetor)-1

  while primeiro <= ultimo:
    meio = (primeiro + ultimo) // 2
    if vetor[meio] == chave:
      ## Item encontrado
      return meio
    
    if chave < vetor[meio]:
      ultimo = meio - 1
    else:
      primeiro = meio + 1
  
  return -1
```



## 

## Considerações

Obter a informação desejada no menor tempo possível é diferencial para a tomada de decisões, além de ser um dos elementos principais na eficiência dos aplicativos, o qual vai ser mais “rápido” se obtiver os dados necessários em menor tempo. 

Vimos que, se os dados não estiverem ordenados de alguma maneira, não temos alternativas de pesquisa e temos que realizar uma pesquisa em cada um dos elementos para verificar sua existência ou ausência. 

Foram, também, apresentados alguns algoritmos de pesquisa em conjunto de dados ordenados. A pesquisa sequencial visita os elementos, a partir do primeiro, um após o outro até encontrar a chave desejada, ou, se encontrar um valor maior que o pesquisado, interrompe a procura. 

A pesquisa binária divide o conjunto de dados em duas partes e continua procurando pela chave na parte que potencialmente ela existiria. É eleita a metade da esquerda se a chave for menor que o elemento central, caso contrário, a metade da direita é escolhida. 



