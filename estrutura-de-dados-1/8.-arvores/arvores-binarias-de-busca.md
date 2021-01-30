# Árvores Binárias de Busca

## Árvores Binárias de Busca

Uma importante aplicação de árvores binárias é a pesquisa. A finalidade desta árvore é estruturar os dados de tal maneira que possibilite uma pesquisa binária.

São consideradas árvores binárias de busca as estruturas que obedecem às seguintes características:

a\) todas as chaves da subárvore esquerda são menores que a chave da raiz;   
b\) todas as chaves da subárvore direita são maiores que a chave raiz; e  
c\) as subárvores direita e esquerda são também árvores binárias de busca.

Essa estrutura possibilita que a busca por uma determinada chave seja realizada com um número menor de comparações. A busca de uma chave “n” segue os seguintes passos:

a\) inicialmente compare com a raiz;   
b\) se menor, vá para a subárvore esquerda; e  
c\) se maior, para a subárvore direita.

![](../../.gitbook/assets/image%20%2852%29.png)

Sabendo que a árvore acima é uma árvore binária de busca, para encontrarmos a chave “H” vamos percorrer os seguintes nós: B -&gt; J -&gt; F -&gt; H.

Assim, começando pela raiz temos: H é maior que B, segue a subárvore da direita; “H” é menor que “J”, segue a subárvore da esquerda; “H” é maior que “F”, segue a subárvore da direita e finalmente encontramos a chave.

### Inserção em árvores binárias de busca

As operações em árvores binárias devem satisfazer as regras que as definem, isto é, todas as chaves da subárvore esquerda devem ser menores que a chave da raiz e todas as chaves da subárvore direita devem ser maiores que a chave da raiz.

Depois de realizada uma inserção, a árvore deverá manter suas características. Para inserir um nó na árvore, são necessários os seguintes passos:

* Pesquisar a chave a ser inserida; e
* Se não achar, inserir no último nó da pesquisa.

No exemplo abaixo, a chave 5 deve ser inserida na árvore:

![](../../.gitbook/assets/image%20%2855%29.png)



Realizamos a pesquisa da chave 5 e, inicialmente, comparamos com a raiz 6. Como o 5 é menor, vamos pela subárvore à esquerda. Comparamos com o nó 2 e, como 5 é maior, vamos pela direita, onde comparamos com o 4 e, como 5 é maior, vamos pela direita. Como o nó 4 é uma folha, não temos mais como caminhar e, então, inserimos o novo nó.

### Remoção em árvores binárias de busca

A operação de remoção de um nó é mais complexa e envolve alguns arranjos na árvore binária. De acordo com a posição do nó a ser removido, temos três condições que devem ser observadas:

a\) se o nó é folha, apenas remover imediatamente;

b\) se possuir um filho, pode ser removido após os ajustes do ponteiro de seu pai, isto é, seu pai deverá apontar para seu filho; e

c\) se o nó possuir dois filhos, deve-se substituir este nó com o nó da subárvore à direita que possuir a chave com o menor valor e remover aquele nó. Como o menor nó da subárvore direita não pode ter um filho à esquerda, a sua remoção segue a condição do item “a”.

![](../../.gitbook/assets/image%20%2858%29.png)

![](../../.gitbook/assets/image%20%2853%29.png)

### 

### Exemplos de Implementação

[https://colab.research.google.com/drive/1zhIhUNME8RiJNG6UFLALwTXiCuvsWZDY\#scrollTo=nt0tZCZ7hkap](https://colab.research.google.com/drive/1zhIhUNME8RiJNG6UFLALwTXiCuvsWZDY#scrollTo=nt0tZCZ7hkap)

