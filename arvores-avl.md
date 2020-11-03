# Árvores AVL

### Árvores Balanceadas

Árvores de pesquisa devem manter uma simetria entre as subárvores da direita e esquerda de sua raiz e assim sucessivamente para cada nó. Isso possibilita uma maior eficiência na procura de uma chave. Uma árvore que possua um dos lados muito maior que o outro \(desbalanceada\) perde sua eficiência na pesquisa, pois, temos que percorrer muitos nós, em sequência, para encontrar uma chave posicionada nas folhas.

Uma árvore é considerada balanceada se, para cada nó, as alturas de suas subárvores diferem de, no máximo, 1.

Considere os seguintes exemplos de árvore binária:

![](.gitbook/assets/image%20%2854%29.png)

Árvore 01: está desbalanceada, pois, considerando o nó 6, a altura da subárvore esquerda é igual a 3 e a altura da subárvore direita é igual a 1, a diferença 3 – 1 = 2.

Árvore 02: está balanceada, pois todas as subárvores de cada nó têm diferença de altura em no máximo 1.

A inserção de chaves em uma árvore binária poderá provocar o seu des- balanceamento, o que pode tornar a busca tão ineficiente quanto a busca sequencial \(no pior caso\). A solução neste caso seria o balanceamento da árvore quando necessário.

Considerando a Árvore 02 representada acima, insira a chave 10. Teríamos o seguinte resultado:

![](.gitbook/assets/image%20%2857%29.png)

Teríamos como resultado uma árvore binária desbalanceada. Uma vez que a altura da subárvore à direita do nó 8 é 2 e a altura da sua subárvore à esquerda é 0, portanto, teríamos uma diferença maior que 1.

#### Balanceamento de árvores binárias

Árvores AVL foram propostas pelos matemáticos russos \(G.M. **A**delson-**V**el-skki e E.M. **L**andis\). Após as operações de inserção e remoção, podemos gerar o desbalanceamento da árvore. Nestes casos, precisamos nos preocupar em reparar o seu balanço. A restauração deste balanço é efetuada através de operações chamadas de rotações.

{% hint style="info" %}
Acesse o link para ver uma animação do balanceamento de uma árvore após as operações de inserção e remoção: [https://www.cs.usfca.edu/~galles/visualization/AVLtree.html](https://www.cs.usfca.edu/~galles/visualization/AVLtree.html)
{% endhint %}

Como já vimos, uma árvore é dita balanceada se a diferença entre a altura da subárvore à direita e a altura da subárvore à esquerda for no máximo 1. A esta condição damos o nome de fator de balanceamento \(FB\).

**Balanceamento:**

1º - Calcular o fator de balanceamento de cada nó FB\(nó\) = \(altura da subárvore à direita – altura da subárvore à esquerda\)

2º - Para uma árvore ser AVL, os fatores de balanço devem ser necessariamente -1, 0, ou 1;

3º - O nó com FB &gt;1 ou &lt;-1 deve ser balanceado. O balanceamento de um nó é feito através de operações denominadas rotações. Substituição de um nó raiz por um de seus filhos, descendo este um nível:

a. Rotação simples: os sinais do FB do nó desbalanceado e de seu filho são iguais, isto é, ambos negativos ou positivos. Exemplo, \(+2 e +1\) ou \(-2 e -1\). Neste caso, o nó filho deve ser posicionado no lugar da raiz da subárvore. A rotação pode ser à direita, quando o nó filho à esquerda toma o lugar da raiz ou à esquerda, quando o nó filho à direita toma o lugar da raiz.

b. Rotação dupla: os sinais do FB do nó desbalanceado e de seu filho são diferentes, isto é, um positivo e outro negativo. Exemplo, \(+2 e -1\) ou \(-2 e +1\). Neste caso, devemos realizar, inicialmente, uma rotação na subárvore do nó filho e em seguida fazer uma rotação simples.

**Rotação simples:**

![](.gitbook/assets/image%20%2856%29.png)

Em alguns casos as operações de rotação necessitam de remanejamento de nós para manter a característica da árvore binária de busca. Veja o exemplo abaixo:

![](.gitbook/assets/image%20%2860%29.png)

Após a inserção do nó 1, o nó 6 tornou-se desbalanceado. Ao realizar a rotação do nó 3, seu filho, o nó 4, deve ser reposicionado na subárvore à direita.

**Rotação Dupla:**

![](.gitbook/assets/image%20%2859%29.png)

No caso acima, o nó 6 está desbalanceado, FB\(6\) = -2 e o FB\(3\) = 1 e, como os sinais estão trocados, devemos realizar a rotação dupla. Primeiramente, realizamos a rotação simples do nó 4 com o nó 3 e fazemos os ajustes necessários e, em seguida, realizamos a rotação simples do nó 4 com o nó 6 e fazemos os ajustes necessários.

