# Lista Duplamente Encadeada

As listas duplamente encadeadas são uma extensão da lista encadeada ligada apresentada no item anterior.

Uma lista duplamente encadeada é formada por um conjunto de nós composto normalmente por três elementos: uma variável que armazena a informação \(`carga`\), podendo ser objetos, números, caracteres etc. e dois ponteiros que possibilitam a ligação entre os nós anterior \(`anterior`\) e posterior  \(`próximo`\) desta lista.

Assim, enquanto que em uma lista encadeada simples, cada nó conhece apenas o próximo nó, nas listas duplamente encadeadas, os nós conhecem também o seu antecessor, com exceção da cabeça, que aponta apenas para o seu sucessor e da cauda, que  aponta apenas para o seu antecessor.

Este tipo de solução permite percorrer uma lista nas duas direções. Por exemplo, do início \(CABEÇA\) até o final da lista \(CAUDA\),utilizaremos o ponteiro PRÓXIMO. Para percorrer a lista do final até o início \(i.e., ordem inversa\), devemos começar pelo último nó \(CAUDA\) e, através do ponteiro ANTERIOR, percorrer a lista até encontrar o primeiro nó \(CABEÇA\).

A figura a seguir mostra a representação gráfica de uma lista duplamente encadeada. Note que agora há a presença do ponteiro `ant`\(destacado em verde\), que referencia o elemento anterior, o que possibilita a navegação nos dois sentidos. 

![Representa&#xE7;&#xE3;o gr&#xE1;fica de uma lista duplamente encadeada](https://documents.app.lucidchart.com/documents/7d076ce8-dc0b-4063-b982-fe8d34cbf2d4/pages/0_0?a=1519&x=-5&y=3181&w=1870&h=269&store=1&accept=image%2F*&auth=LCA%2011494295ed421b5f2da0f965779d7dd41203f429-ts%3D1599922486)

## Implementação de uma lista duplamente encadeada

Da mesma forma que a lista encadeada simples, vamos precisar utilizar o objeto `No` para descrever cada elemento, e um objeto `ListaEncadeada`  que irá conter a referência para a cabeça e a cauda. A diferença é que agora o objeto `No` precisará conter um atributo a mais que irá referenciar o elemento anterior, que chamaremos de `ant`.   

```text
class No:
    def __init__(self, carga: object = None, ant: 'No' = None, prox: 'No' = None):
        self.carga = carga
        self.prox = prox
        self.ant = ant

    def __str__(self):
        return str(self.carga)
```

Vamos agora ver como funcionam as operações de inserção e remoção na lista duplamente encadeada considerando a seguinte lista:

![](../.gitbook/assets/image%20%2826%29.png)

### Inserir no início

Para inserir no início da lista duplamente encadeada, devem ser realizados os seguintes passos:

1. Atualizar o ponteiro `prox` do novo nó a ser inserido para apontar para a cabeça atual
2. Mudar o apontador `cabeca` da lista para apontar para o nó novo
3. Mudar o apontador `ant` da antiga cabeça \(agora segundo nó da lista\) para apontar para a nova cabeça

![](../.gitbook/assets/image%20%2824%29.png)

```text
    def inserir_no_inicio(self, valor: object):
        novo: 'No' = No(valor)
        if self.cabeca is None:
            self.cabeca = self.cauda = novo
        else:        
            novo.prox = self.cabeca
            self.cabeca = novo
            novo.prox.ant = novo
```

### Inserir no final

Para inserir no final, seguimos as seguintes etapas:

1. Atribuir o apontador do anterior \(`ant`\) do novo elemento para a cauda atual
2. Atualizar o elemento `prox` da cauda atual para referenciar o novo nó
3. Atualizar a cauda da lista para apontar para o novo nó

![](../.gitbook/assets/image%20%2828%29.png)

```text
    def inserir_no_final(self, valor):
        novo: 'No' = No(valor)
        if self.cabeca is None:
            self.cabeca = self.cauda = novo
        else:
          novo.ant = self.cauda # O anterior do nó novo será a cauda atual
          novo.ant.prox = novo # O próximo do elemento anterior será o novo elemento a ser inserido
          self.cauda = novo # a cauda passa a ser o elemento novo a ser inserido
```

{% hint style="info" %}
Em ambos os casos, se lista estiver vazia, o novo elemento  ser inserido é atribuído tanto à cauda como à cabeça \(linha 4\)
{% endhint %}

### Remover do início

Para remover um elemento do início da lista, devemos seguir as seguintes etapas:

1. Atualizar a cabeça da lista para ser o seu próximo elemento
2. Mudar o apontador anterior da cabeça atual \(`ant` \) para apontar para `None`, visto que agora ele tornou-se o primeiro nó da lista. 

![](../.gitbook/assets/image%20%2827%29.png)

Note que agora o elemento que era a cabeça anteriormente não é apontado mais por nenhum elemento, logo ele será descartado pelo coletor de lixo.

```text
    def remover_do_inicio(self):
        if self.cabeca is None:
            print("Lista vazia")
            return
        
        if self.cabeca == self.cauda:
            self.cabeca = self.cauda = None
        else:
            self.cabeca = self.cabeca.prox 
            self.cabeca.ant = None # O anterior da nova cabeça agora passa a apontar para Non
```

### Remover do final

Para remover um elemento do final, diferentemente do que era necessário na lista encadeada simples, não precisaremos mais percorrer a lista até o final. Como agora temos o apontador pro elemento anterior \(`ant` \), podemos acessar diretamente a cauda e mudar o seu anterior para remover a referência para o próximo nó. Desta forma, o desempenho desta operação deixa de ser O\(n\) \(tempo linear\) para ser O\(1\) \(tempo constante\). 

Para tal, devemos as seguintes etapas:

1. Mudar o apontador da cauda da lista para apontar para o seu anterior \(penúltimo elemento\)
2. Mudar o apontador `prox` da nova cauda para apontar para `None`

![](../.gitbook/assets/image%20%2823%29.png)

```text
    def remover_do_final(self):
        if self.cabeca is None:
            print("Lista vazia")
            return
        
        if self.cabeca == self.cauda:
            self.cabeca = self.cauda = None
        else:
            # Note que agora não é mais necessário percorrer a lista até o final, basta começar navegando pela cauda
            self.cauda = self.cauda.ant # Faz a cauda apontar agora para o penúltimo elemento da lista
            self.cauda.prox = None # o próximo da nova cauda agora passa a pontar para None
```

### Percorrer na ordem inversa

Agora que temos o ponteiro que aponta para o nó anterior \(`ant`\), torna-se bem mais fácil percorrer a lista no sentido inverso \(do último até o primeiro\). Para tal, utilizamos a mesma lógica do método imprimir da lista encadeada: criar uma variável temporária `atual` que irá receber cada elemento da lista dentro de um `while`. Porém, ao invés de atribuir inicialmente a variável `atual`   ao elemento cabeça e ir atribuindo o valor de atual ao seu próximo a cada iteração, iremos inicializar a variável atual recebendo a cauda e a cada iteração atribuir ela ao seu anterior.

```text
    def imprimir_invertido(self):
        atual: 'No' = self.cauda # inicializa atual apontando para a cauda
        while atual is not None:
            print(atual.carga) 
            atual = atual.ant # a cada iteração, atribui atual ao seu anterior
```

### Exemplos

* [Notebook com exemplos da implementação de uma lista duplamente encadeada](https://colab.research.google.com/drive/1sRuNNuolb8BHnC4L67QmevtmvIf5Ytip#scrollTo=e26WQKULmnxZ) 

