# Lista Encadeada Simples

Uma lista encadeada \(ou lista ligada\) dinamicamente é uma estrutura de dados linear e dinâmica. Ela é composta por um conjunto de nós, cada nó possuindo dois elementos: o primeiro armazena informações e o segundo armazena um ponteiro que guarda informação do endereço \(referências a endereços de memória\) para o próximo nó na lista.

Em uma implementação de lista encadeada, cada nó \(item\) da lista é ligado com o seguinte através do ponteiro \(uma variável com o valor do endereçamento para o próximo nó\). Isso significa dizer que cada nó da lista contém o registro de dados \(informações\) e uma variável que aponta para o próximo nó. Este tipo de implementação permite utilizar posições não contíguas de memória, sendo possível inserir e retirar elementos sem haver a necessidade de deslocar os nós seguintes da lista.

![Representa&#xE7;&#xE3;o gr&#xE1;fica da lista encadeada](../.gitbook/assets/image%20%2813%29.png)

A cabeça em uma lista encadeada representa o seu primeiro elemento e pode ser guardada em uma variável. A cauda representa o último elemento a qual também pode ser guardada em uma variável. Assim, conhecemos, inicialmente, dois elementos da lista: o primeiro e o último. Se desejarmos manipular a lista, devemos inicialmente nos referenciar a estas variáveis e, a partir delas, percorrer a lista para identificar o restante.

O limite para a alocação dinâmica é diretamente proporcional à quantidade de memória física que está disponível na máquina, valendo, também, o tamanho do espaço físico disponível dentro do sistema de memória virtual.

A seguir apresentamos as vantagens e desvantagens entre a lista encadeada e as listas estáticas.

**Vantagens**

* A inserção ou remoção de um elemento na lista não implica a mudança de lugar de outros elementos;
* Não é necessário definir, no momento da criação da lista, o número máximo de elementos da lista. É́ possível alocar memória "dinamicamente, apenas para o número de nós necessários.

**Desvantagens**

* A manipulação torna-se mais "perigosa" uma vez que, se o encadeamento \(ligação\) entre elementos da lista for mal feito, toda a lista pode ser perdida;
* Para acessar o elemento na posição n da lista, deve-se percorrer os `n-1` anteriores.

## Implementação de uma lista encadeada simples

A implementação a seguir utiliza os conceitos de Orientação a Objeto para criar a lista. Para tal, temos duas classes: `No` e `Lista`.

Inicialmente, criamos uma Classe `No` e ela será a nossa base para a alocação dinâmica para representar cada elemento da lista. O `No` contém dois atributos fundamentais: o campo `carga` para receber a informação armazenada em cada item e `prox` para referenciar o próximo objeto da nossa lista.

```text
class No:
    def __init__(self, carga, prox: 'No' = None):
        self.carga = carga
        self.proximo = prox

    def __str__(self):
        return str(self.carga)
```

Alguns conceitos importantes relacionados à atribuição de valores a objetos:

### Criação e ligação entre nós

```text
n1: 'No' = No("aa") 
```

ou

```text
n1: 'No' = No()
n1.carga = "aa"
```

![](../.gitbook/assets/image%20%2821%29.png)

```text
n2: 'No' = No()
n2.carga = "bb"
```

![](../.gitbook/assets/image%20%2819%29.png)

```text
n1.prox = n2
```

Note que `n1.prox = n2` atribui o endereço de `n2` ao atributo `prox` do nó `n1`. Assim, o `prox` de `n1` apontará para `n2`.

### **Declaração da Lista**

A classe Lista possui três atributos principais: **cabeça** \(indica o início da lista, declarado como sendo do tipo No\), **cauda** \(indica o fim da lista, também declarado como sendo do tipo No\) e **nomeDaLista**.

Perceba que a lista é “composta” apenas de dois nós \(cabeça e cauda\). Na verdade, é o que basta para manipularmos a lista. Não precisamos conhecer o restante, pois a partir do primeiro elemento podemos percorrer toda a lista, seguindo o conceito de que cada nó conhece o seu sucessor. Assim, o primeiro sabe qual é o próximo e assim sucessivamente, até chegarmos ao último \(**cauda**\).

```text
class ListaEncadeada:
    def __init__(self):
        self.cabeca = None
        self.cauda = None
```

Agora que temos a estrutura básica para uma lista encadeada declarada, podemos começar a trabalhar com algumas operações, como inserção e remoção.

### Inserir no início

Considere a seguinte lista:

![](../.gitbook/assets/image%20%2816%29.png)

Para inserir um elemento no início da lista, é preciso alterar a cabeça da list para apontar para o novo nó e apontar para o nó que era cabeça anteriormente como sendo o próximo do novo.

![](../.gitbook/assets/image%20%2810%29.png)

```text
    def inserir_valor_no_inicio(self, valor):
        novo = No(valor)
        if self.cabeca == None:
            self.cabeca = self.cauda = novo
        else:
            novo.prox = self.cabeca
            self.cabeca = novo
```

{% hint style="info" %}
Se a lista estiver vazia, o novo elemento a ser inserido é referenciado tanto como cabeça, como cauda \(linha 9\)
{% endhint %}

Utilizando o novo método para inserir o valor "novo" no início da lista:

```text
lista = ListaEncadeada(n1, n2)
lista.inserir_valor_no_inicio("novo")
```

### Inserir no final

Para inserir no final, é preciso acessar o último elemento da lista \(cauda\) e apontar para o novo elemento como o seu próximo. Em seguida, é preciso mudar a referência da cauda na lista para apontar para o novo elemento que está sendo inserido.

```text
    def inserir_valor_no_final(self, valor):
        novo = No(valor)
        if self.cabeca == None:
            self.cabeca = self.cauda = novo
        else:
            self.cauda.prox = novo
            self.cauda = novo
```

![](../.gitbook/assets/image%20%2818%29.png)

### Imprimir elementos da lista

Para imprimir todos os elementos da lista é preciso percorrer toda a lista retornando as informações que estão na carga de cada nó. Para percorrer uma lista encadeada, usamos o atributo `prox` de cada nó até que a referência pra ele seja `None`.

Considere o seguinte exemplo:

![](../.gitbook/assets/image%20%2817%29.png)

A lista possui os nós  n1 como cabeça e n4 como cauda. Como conhecemos o inicio da lista, basta seguí-la através do atributo `prox` até chegar no último. Para isso, normalmente utilizamos uma variável \(`atual`\) que vai sendo associada a cada nó da lista.    

```text
    def imprime_lista(self):
        atual = None
        if self.cabeca == None:
            print("Lista vazia")
            return
        
        atual = self.cabeca
        while atual != None:
            print(atual.carga + " ")
            atual = atual.prox
```

### Remover elemento do início



### Remover elemento do final



### Exemplos e Exercícios

* [Exemplos e exercícios](https://colab.research.google.com/drive/1fAtHIKKEf6yZFQmVCeTNDrS7tE7P3DCl?usp=sharing)

