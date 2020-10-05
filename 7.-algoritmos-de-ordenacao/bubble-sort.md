# Bubble Sort

### Algoritmo de Ordenação da Bolha \(_Bubble Sort_\) 

O algoritmo _Bubble Sort_ utiliza a técnica chamada de ordenação por submersão \(_sinking sort_\) e funciona da seguinte forma: os valores maiores submergem para o final da lista. Ao mesmo tempo, os valores menores sobem gradualmente até o topo do lista \(em direção ao início do lista\).

Esse algoritmo faz várias passagens pela lista. Cada passagem compara sucessivos pares de elementos. Se um par está em ordem crescente, os valores permanecem na mesma ordem. Se um par está em ordem decrescente, é realizada a troca entre os elementos do par.

Em cada passagem, o elemento maior será “levado” até o final da lista e, assim, iremos percorrer na primeira passagem todos os elementos. Na segunda passagem, não necessitamos percorrer todos, pois o maior estará no final e, então, percorremos até o penúltimo e assim sucessivamente até que a quantidade de elementos a percorrer seja igual a 1. Temos, então, o vetor ordenado.

Exemplo: dado o seguinte vetor desordenado como entrada, vamos acompanhar as etapas de execução do _Bubble Sort_: 

![](https://documents.lucid.app/documents/a0dd1809-658d-449d-9c21-1cc85c033669/pages/0_0?a=549&x=34&y=125&w=719&h=110&store=1&accept=image%2F*&auth=LCA%20b0ee55369bcdd2e3b57dca50eafec42dc127f3f6-ts%3D1601721229)

Cada elemento do vetor é percorrido e a cada passagem são comparados os pares de elementos \(o atual com o próximo\). Caso o atual seja maior que o próximo, eles trocam de posição.

![](https://documents.lucid.app/documents/a0dd1809-658d-449d-9c21-1cc85c033669/pages/0_0?a=549&x=34&y=204&w=719&h=352&store=1&accept=image%2F*&auth=LCA%2064234ec35eba4d1b2e877fd918ade4cb3429a73f-ts%3D1601721229)

Repare que o vetor já está “um pouco mais ordenado” e o maior elemento ocupa a última posição. Mas ainda não está completamente ordenado. Esse processo então se repete `n` vezes até que o vetor esteja completamente ordenado.

![](https://documents.lucid.app/documents/a0dd1809-658d-449d-9c21-1cc85c033669/pages/0_0?a=549&x=34&y=524&w=719&h=352&store=1&accept=image%2F*&auth=LCA%2013ae6b0fc67c27b99af8418d0f27e6fefe70676f-ts%3D1601721229)

No caso deste exemplo, apenas com duas rodadas foi possível ordenar completamente o vetor. Entretanto, no pior caso seria necessário executar um número de rodadas igual ao tamanho da lista, o que seria representado pela notação O\(n²\).

![Ilustra&#xE7;&#xE3;o do funcionamento do algoritmo Bubble Sort](../.gitbook/assets/bubble-sort-example-300px.gif)

#### Implementação do Bubble Sort

```text
def bubble_sort_alg(vetor):
    trocou: bool = True
    ultimo: int = len(vetor)-1
    while ultimo > 0 and trocou:
        trocou = False
        for i in range(atual):
            if vetor[i] > vetor[i+1]:
                trocou = True
                aux = vetor[i]
                vetor[i] = vetor[i+1]
                vetor[i+1] = aux
        ultimo -= 1
```

Note que enquanto há trocas \(`trocou==true`\) o algoritmo continua iniciando uma nova rodada que irá varrer toda a lista em busca de trocar a posição dos pares de elementos que estão em ordem decrescente. Como o último elemento da lista sempre será o maior a cada rodada, pode-se retirá-lo da comparação para melhorar um pouco o tempo de execução. Para isso, usamos a variável `ultimo,`que recebe inicialmente como valor a posição do último elemento e é decrementada em menos 1 a cada rodada.

