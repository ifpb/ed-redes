# Árvores Binárias de Busca

### Árvores Binárias de Busca

Uma importante aplicação de árvores binárias é a pesquisa. A finalidade desta árvore é estruturar os dados de tal maneira que possibilite uma pesquisa binária.

São consideradas árvores binárias de busca as estruturas que obedecem às seguintes características:

a\) todas as chaves da subárvore esquerda são menores que a chave da raiz;   
b\) todas as chaves da subárvore direita são maiores que a chave raiz; e  
c\) as subárvores direita e esquerda são também árvores binárias de busca.

Essa estrutura possibilita que a busca por uma determinada chave seja realizada com um número menor de comparações. A busca de uma chave “n” segue os seguintes passos:

a\) inicialmente compare com a raiz;   
b\) se menor, vá para a subárvore esquerda; e  
c\) se maior, para a subárvore direita.

![](.gitbook/assets/image%20%2852%29.png)

Sabendo que a árvore acima é uma árvore binária de busca, para encontrarmos a chave “H” vamos percorrer os seguintes nós: B -&gt; J -&gt; F -&gt; H.

Assim, começando pela raiz temos: H é maior que B, segue a subárvore da direita; “H” é menor que “J”, segue a subárvore da esquerda; “H” é maior que “F”, segue a subárvore da direita e finalmente encontramos a chave.

