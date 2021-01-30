# Ordenação

A classificação \(ordenação\) é um dos processos mais utilizados na computação.

A classificação compreende um processo de rearranjar um conjunto de dados de acordo com certa relação de ordens dentre as quais podemos citar:

* ordem alfabética;
* ordem numérica; e
* ordem cronológica.

Os tipos de ordenação acima podem ser dispostos de duas maneiras: ordem crescente, que rearranja os elementos do menor para o maior, e ordem decrescente, que rearranja os elementos do maior para o menor. Aqui, iremos considerar a ordem crescente para as implementações realizadas.

Classificar dados, isto é, colocar os dados em ordem crescente ou decrescente, é essencial para a eficiência de algumas aplicações. Todos os algoritmos aqui estudados terão o mesmo resultado final: o vetor de dados classificado. A escolha do algoritmo afetará, principalmente, o tempo de execução e o uso de memória do programa. Os algoritmos da bolha, da seleção e da inserção \(direta e binária\) são simples de programar, porém não são tão eficientes. O método de classificação _quicksort_ é o mais eficiente, mas também, é mais complicado de se implementar.

Para suporte e posteriores testes da implementação dos algoritmos, vamos ver uma forma de criar um vetor com valores aleatórios:

### Implementação de um vetor com números aleatórios

Para servir de base para os exemplos das próximas seções, vamos utilizar a seguinte função para gerar uma lista com números aleatórios:

```text
import random
def lista_numeros_aleatorios():
    lista = random.sample(range(0,99), 10)
    return lista
    
print(lista_numeros_aleatorios()
```

A função `sample` do pacote `random` recebe como primeiro parâmetro o intervalo que os números serão gerados \(nesse caso, de 0 a 99\) e o segundo parâmetro recebe a quantidade de números que devem ser gerados.

### Algoritmos de Ordenação

* [Bubble Sort](bubble-sort.md)
* [Selection Sort](selection-sort.md)
* [Insertion Sort](insertion-sort.md)



