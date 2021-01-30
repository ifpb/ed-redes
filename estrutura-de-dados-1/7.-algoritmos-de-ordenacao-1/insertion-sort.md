# Insertion Sort

### Inserção direta \(_Insertion Sort_\)

O algoritmo de ordenação inserção direta é considerado o mais rápido entre os algoritmos considerados simples: bolha e seleção direta.

A principal característica da inserção direta está em ordenar o conjunto de elementos a partir de um subconjunto ordenado localizado em seu início \(os dois primeiros elementos\) e, a cada novo passo, é acrescentado a este subconjunto mais um elemento na posição adequada para se manter a ordem, até que o último elemento do conjunto seja selecionado e inserido, concluindo a ordenação do vetor.

A primeira iteração seleciona os dois primeiro elementos do vetor e, se o segundo elemento for menor que o primeiro elemento, o permuta pelo primeiro elemento \(ou seja, ordena apenas os dois primeiros elementos da lista\). 

A segunda iteração seleciona o terceiro elemento e o insere na posição correta com relação aos dois primeiros elementos de modo que todos os três elementos estejam em ordem. E, assim, sucessivamente para os demais elementos.

Neste algoritmo, ao se procurar o local ideal para inserir o novo elemento entre os elementos já ordenados, pode-se optar por uma busca sequencial ou pela busca binária.

![](https://documents.lucid.app/documents/a0dd1809-658d-449d-9c21-1cc85c033669/pages/0_0?a=968&x=1389&y=115&w=724&h=550&store=1&accept=image%2F*&auth=LCA%20a8a18c509f1fb8a700ff136504a82909b4099217-ts%3D1601807442)

Podemos perceber que ao inserirmos um elemento entre o subconjunto de elementos já ordenados, precisamos realizar o deslocamento uma casa à direita de todos os elementos que forem maiores que ele.

![Ilustra&#xE7;&#xE3;o do funcionamento do algoritmo Insertion Sort](../../.gitbook/assets/insertion-sort-example%20%281%29.gif)

#### Implementação do _Insertion Sort_

```text
def insertion_sort_seq(lista: List):
    for i in range(1, len(lista)):
        chave = lista[i]
        j = i - 1
        while j >= 0 and chave < lista[j]:
            lista[j+1] = lista[j]
            j -= 1
        lista[j+1] = chave

```

Note que a cada rodada busca-se a posição o elemento que será inserido, fazendo o deslocamento de toda a lista para abrir espaço para a inserção do elemento na ordem correta.

