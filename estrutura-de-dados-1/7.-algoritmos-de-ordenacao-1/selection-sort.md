# Selection Sort

### Algoritmo de Seleção direta \(_Selection Sort_\)

Tal como o algoritmo anterior, a seleção direta percorre várias vezes o vetor. A primeira iteração do algoritmo seleciona o menor elemento e o permuta pelo primeiro elemento. A segunda iteração seleciona o segundo menor elemento \(que é o menor item dos elementos restantes\) e o permuta pelo segundo elemento. E, assim, sucessivamente até o penúltimo elemento.

Cada iteração percorre um elemento a menos no vetor, isto é, na primeira todos os elementos são visitados, na segunda, visitamos a partir do segundo elemento, pois o primeiro irá conter o menor elemento. Assim, sucessivamente, vamos percorrendo os trechos menores do vetor, até chegarmos aos dois últimos elementos. Quando encontramos o menor entre os dois últimos, o vetor estará ordenado.

![](https://documents.lucid.app/documents/a0dd1809-658d-449d-9c21-1cc85c033669/pages/0_0?a=820&x=714&y=110&w=719&h=576&store=1&accept=image%2F*&auth=LCA%20082dc814f8605fcb59a2cc4b1df04bf79765f095-ts%3D1601807442)

A ideia básica desse algoritmo é procurar o menor nó a cada rodada e mover ele pro início da lista. A cada nova rodada, considera-se o início da lista como sendo uma posição à frente, de maneira que em `n` rodadas todos os menores elementos tenham sido posicionados no início, fazendo a lista ficar ordenada.

![Ilustra&#xE7;&#xE3;o do funcionamento do Selection Sort](../../.gitbook/assets/selection-sort-animation.gif)

#### Implementação do _Selection Sort_

```text
def selection_sort_alg(vetor: List):
    for i in range(len(vetor)):
        pos_menor = i
        menor = vetor[i]
        for j in range(i+1, len(vetor)):
            if vetor[j] < menor:
                menor = vetor[j]
                pos_menor = j
        vetor[pos_menor] = vetor[i]
        vetor[i] = menor
```

Note que a cada rodada o menor elemento da lista é movido para o início. Ao término da rodada, o primeiro elemento a ser considerado é deslocado uma posição à direita, fazendo com que ao concluir as `n`  rodadas a lista esteja ordenada. Como esse algoritmo percorre a lista  `n`  vezes, tal como o _Bubble Sort_, sua complexidade também é O\(n²\).

