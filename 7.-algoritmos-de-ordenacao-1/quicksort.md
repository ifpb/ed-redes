# Quicksort

Assim como o Merge Sort, o Quicksort é um algoritmo recursivo que aplica o conceito de divisão e conquista. No entanto, seu funcionamento é um pouco diferente. No Merge sort, o passo da divisão apenas separa os elementos nos vetores da esquerda e direita, ocorrendo todo o trabalho de ordenação na etapa de combinação. No Quicksort é o oposto: todo o trabalho acontece na etapa da divisão, enquanto que a etapa de combinar apenas junta o resultado.

O quicksort tem algumas outras diferenças em relação ao merge sort: funciona localmente \(sem precisar de criar vetores com cópias dos elementos\) e seu tempo de execução no pior caso é tão ruim quanto o das ordenações por seleção e por inserção: O\(n²\). No entanto, seu tempo de execução médio é tão bom quanto o merge sort: O\(n log n\). Então, por que pensar em quicksort quando o merge sort é, pelo menos, igualmente bom? Porque o fator constante oculto na notação Big-O do Quicksort é muito bom, de maneira que, na prática, o Quicksort tem desempenho melhor do que o merge sort, e é significativamente melhor do que os algoritmos de seleção e de inserção.

O Quicksort usa a divisão e conquista da seguinte forma:

**Divisão:** divide-se o vetor a partir de um determinado elemento escolhido na lista. Esse elemento é chamado de **pivô**. Os elementos são reorganizados em de maneira que todos os elementos em que são menores ou iguais ao pivô fiquem à esquerda e que todos os elementos em fiquem à direita do pivô. Esse procedimento é chamado de **particionamento**. Nesse ponto, não importa a ordem que os elementos à esquerda do pivô estão em relação entre eles, e o mesmo vale para os elementos à direita. Apenas deve-se preocupar que cada elemento esteja do lado correto do pivô. 

**Conquista:** ordena-se recursivamente as subarrays com todos os elementos à esquerda do pivô \(os  devem ser menores ou iguais ao pivô\) e todos os elementos à direita do pivô \(que devem ser maiores que o pivô\).

**Combinar:** uma vez que a etapa da conquista ordena recursivamente, o vetor já estará ordenado. Visto que todos os elementos à esquerda do pivô são menores ou iguais ao pivô e estão ordenados, e todos os elementos à direita do pivô, são maiores que o pivô e estão ordenados. 

![](../.gitbook/assets/image%20%2836%29.png)

### Implementação

Para facilitar a compreensão e simplificar a implementação do algoritmo, foi utilizado o recurso de [compreensão de listas](https://www.codingame.com/playgrounds/52499/programacao-python-intermediario---prof--marco-vaz/compreensao-de-listas-exemplos) em Python.

Neste exemplo, foi escolhido como pivô o primeiro elemento. Note que a implementação do particionamento consiste em extrair um subconjunto da lista original. No caso, foram extraídos três, contendo os elementos iguais, menores e maiores do que o pivô. O particionamento é chamado recursivamente até que o tamanho do vetor seja 1, e o retorno final era ser a composição de todos os vetores particionados, trazendo o resultado ordenado. 

```text
def quicksort(vetor):
    if len(vetor) <= 1: return vetor
    pivo = vetor[0]
    iguais = [x for x in vetor if x == pivo]
    menores = [x for x in vetor if x < pivo]
    maiores = [x for x in vetor if x > pivo]
    return quicksort(menores) + iguais + quicksort(maiores)
```

### Vantagens:  

* Melhor opção para ordenar vetores grandes  
* Muito rápido porque o laço interno é simples  
* Memória auxiliar para a pilha de recursão é pequena  
* Complexidade no caso médio é O \(n lg n\) 

### Desvantagens:  

* Não é estável \(não conhecemos forma eficiente para tornar o quicksort estável\)  
* Pior caso é quadrático \(O\(n²\)\)

### Análise da complexidade:

* Melhor caso: O \( n lg n \)
* Caso médio: O \( n lg n \)
* Pior caso: O\(n²\)

### Otimização:

* Para evitar o pior caso do Quicksort, podemos escolher o pivô como a mediana de três elementos.

