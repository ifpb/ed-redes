# Merge Sort

A ideia básica do Merge Sort é criar uma sequência ordenada a partir de duas outras também ordenadas. Para isso, o algoritmo Merge Sort divide a sequência original em pares de dados, agrupa estes pares na ordem desejada; depois as agrupa as sequências de pares já ordenados, formando uma nova sequência ordenada de quatro elementos, e assim por diante, até ter toda a sequência ordenada.

Algoritmo:  
Os três passos úteis dos algoritmos dividir-para-conquistar, que se aplicam ao Merge Sort são:

1. Dividir: Dividir os dados em subsequências pequenas; Este passo é realizado recursivamente, iniciando com a divisão do vetor de n elementos em duas metades. Cada uma das metades é novamente dividida em duas novas metades e assim por diante, até que não seja mais possível a divisão \(ou seja, sobrem n vetores com um elemento cada\).
2. Conquistar: Classificar as duas metades recursivamente aplicando o merge sort;
3. Combinar: Juntar as duas metades em um único conjunto já classificado.
4. Para completar a ordenação do vetor original de n elementos, faz-se o merge ou a fusão dos sub-vetores já ordenados.

![](../.gitbook/assets/image%20%2837%29.png)

```text
def merge(esquerda, direita, vetor):
    i,j,k = 0,0,0
    while i < len(esquerda) and j < len(direita):
        if esquerda[i] <= direita[j]:
            vetor[k] = esquerda[i]
            i, k = i+1, k+1
        else:
            vetor[k] = direita[j]
            j,k = j+1,k+1
                    
    while i < len(esquerda):
        vetor[k] = esquerda[i]
        i, k = i+1, k+1

    while j < len(direita):
        vetor[k] = direita[j]
        j,k = j+1,k+1
        
        
def mergesort(vetor):
    if len(vetor) < 2: return vetor
    meio = len(vetor) // 2
    esquerda = vetor[:meio]
    direita = vetor[meio:]
    mergesort(esquerda)
    mergesort(direita)
    merge(esquerda, direita, vetor)
```

A desvantagem do Merge Sort é que requer o dobro de memória, ou seja, precisa de um vetor com as mesmas dimensões do vetor que está sendo classificado \(para armazenar as cópias da esquerda e direita\).

### Análise da complexidade

Para analisar a complexidade do Merge Sort, deve-se levar em consideração a complexidade método interno **merge\(\)** e do algoritmo principal que o chama:

* **Método** **merge\(\)**: cada chamada une um total de `direita - esquerda` elementos, que no máximo, é `n`. É feita uma comparação a cada iteração. O total de passos do primeiro while não é mais do que `n` \(dos outros, no pior caso, `n/2`\). Logo, complexidade do método **merge\(\)** é `O(n)`.
* **Merge Sort:** para `n = 1`, `T(1) = 1.`Para `n > 1`, executa-se recursivamente: uma vez `(n/2)` com elementos de um lado e outra vez com os `(n/2)` elementos restantes. Após isso, executa-se  o método **`merge()`**, que executa `n` operações.                                                                 **T\(n\) = T \(n/2\) + T \(n/2\) + n**                                                                        **T\(n\) = O \(n log2 n\)**

\*\*\*\*

