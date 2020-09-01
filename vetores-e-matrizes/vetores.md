# Vetores

Um vetor ou array é uma estrutura de dado linear \(uma única dimensão\), composto por um determinado número \(finito\) de elementos \(uma coleção de variáveis\).

{% hint style="info" %}
 Em algumas linguagens há a limitação de que os itens de um vetor devem ser do mesmo tipo de dado. Na linguagem Python \(que será utilizada aqui para mostrar os exemplos\) é permitido incluir elementos de tipos diferentes \(ex.: String, Inteiro\) em um mesmo vetor. 
{% endhint %}

Um vetor é um conjunto de elementos em que cada elemento desse conjunto é acessado através de um índice. A tabela abaixo representa um vetor de nomes. Nela têm-se os valores Maria, Carlos e Ana, sendo que o índice de Maria é 0, de Carlos é 1 e o de Ana é 2.

| 0 | 1 | 2 |
| :--- | :--- | :--- |
| Maria | Carlos | Ana |

Para que possamos acessar os valores armazenados nesse vetor, temos que chamá-los pelo índice: 0, 1 ou 2.

Acessar os elementos de um vetor é muito rápido, sendo considerado o tempo **constante**, pois o acesso aos elementos é feito pelo seu índice. Entretanto, a operação de remoção de um elemento poderá ser complexa se for necessário que não existam espaços "vagos" no meio do vetor, pois nesse caso é necessário mover uma posição todos os elementos depois do elemento removido.

Por exemplo, para excluir o elemento Carlos:

| 0 | 1 | 2 |
| :--- | :--- | :--- |
| Maria |  | Ana |

Ficará a posição 1 vazia e, assim, teremos que deslocar os elementos a sua direita uma posição:

| 0 | 1 | 2 |
| :--- | :--- | :--- |
| Maria | Ana |  |

Vamos aprender agora como declarar e manipular vetores.

### Declarando Vetores

Para podermos manipular vetores, precisamos que inicialmente seja informado o tipo de dado dos elementos que serão armazenados. A declaração de um vetor pode-se diferenciar em cada linguagem de programação. Aqui, utilizaremos a linguagem Python para representar a declaração.

```text
nomes = []

```

{% hint style="info" %}
Instanciar um vetor constitui em reservar espaço de memória para armazenar os elementos.  Na linguagem Python é possível utilizar o método `append` para inserir dinamicamente o elementos no vetor, mas em outras linguagens \(ex.: Java, C\),  é necessário definir o tamanho do vetor inicialmente 
{% endhint %}

 Para simular a alocação estática de elementos em um vetor, podemos declarar um número inicial de elementos no vetor. Por exemplo:

```python
# Declaração simples deu um vetor chamado "cores" que armazenará elementos do tipo "String"
cores = ["azul", "vermelho", "verde", "amarelo"] 

```

Uma alternativa para pré-alocar um conjunto de elementos em um vetor em Python é utilizar o seguinte artifício:

```python
nomes = [None] * 10  # Aloca 10 posições vazias na vetor
print(cores)
```

A saída da execução será: 

```python
[None, None, None, None, None, None, None, None, None, None]
```

Indicando que foram alocados 10 espaços de memória para armazenar dados no vetor criado. 

### Manipulando Vetores

A manipulação dos vetores se dá através das operações de **inserção**, **consulta** e **remoção**, muitas vezes sendo necessário percorrer os elementos do vetor para encontrar o elemento ou a posição desejada.

#### Inserindo valores

Para armazenar um valor em um vetor, é necessário fornecer um índice que indique a posição que esse elemento irá ocupar, por exemplo:

```python
nomes[0] = "Maria"
nomes[1] = "Carlos"
nomes[2] = "Ana"
```

{% hint style="info" %}
Em Python é possível utilizar o método append, ex.: **`nomes.append("josé")`** e adicionar um elemento dinamicamente ao final do vetor. Um detalhe importante é que agora que o vetor **`nomes`** possui 10 elementos pré-alocados, caso seja utilizado o **`append`** o elemento `"josé"` será inserida na 11ª posição.
{% endhint %}

#### Consultando Valores

Para consultarmos um valor do vetor, basta informar o nome da variável que armazena vetor e o índice \(sua posição\), por exemplo:

```python
nome: str = nomes[2]

```

Este trecho de código irá atribuir à variável “nome” do tipo String o valor “Ana” \(se considerarmos as inserções realizadas anteriormente\).

#### Excluindo Valores

Para excluirmos valores de um vetor em Python, basta utilizar a instrução `del` para a referência da posição do vetor que contenha o elemento que desejamos remover. Exemplo:

```python
del nomes[2] # Remove elemento da posição 2

```

Ao utilizar o `del`, o item será removido de fato da memória e os itens que estão em posições à frente serão deslocados para uma posição a menos.

{% hint style="info" %}
É comum tentar remover um item de um vetor atribuindo a ele o valor `None`, mas desta forma o vetor continuará a armazenar esse elemento. Ao acessar o método `len(lista),`que mostra o tamanho da lista, ele permanecera o mesmo de antes à atribuição dos itens ao valor `None`. 
{% endhint %}

#### Cuidados ao Manipular Vetores

* A posição do primeiro elemento de um vetor é indicada pelo índice 0 \(zero\).
* O último elemento de um vetor de tamanho 10 \(dez\) é o de índice 9 \(nove\).
* Acessar uma posição inválida de um vetor causará um erro na execução de seu programa.

#### Percorrendo um vetor e listando seus valores

Para percorrer \(acessar\) todos os elementos de vetor, utilizaremos o comando “for”, conforme exemplo abaixo:

```python
for item in lista:
    print(item) # Exibe o valor de cada elemento da lista
```

Note que o resultado da execução do trecho anterior vai exibir os **valores** dos elementos que estão na lista. No entanto, pode ser necessário ter acesso aos índices \(ou seja, as posições\), de cada elemento no vetor. Para isto, podemos utilizar o método `enumerate`, conforme exemplificado a seguir.

```python
for indice, valor in enumerate(lista):
    print(Indice =", indice)
    print(Valor =, valor)
```

Em ambos os trechos, todos os elementos do vetor serão escritos no console do sistema.

Podemos também realizar uma busca de um valor dentro do vetor, sem saber se ele existe ou o seu índice. Por exemplo, se desejamos saber em qual índice do vetor está o nome Carlos, e se ele existe:

```python
for indice, nome in enumerate(lista):
    if (nome == "Carlos"):
        print(O nome Carlos está na posição ", indice)
```

Este código percorre o vetor e a cada volta ele compara se o valor é Carlos e, se for, ele escreve no console uma mensagem informando o índice em que ele se encontra. Caso não exista, nada será escrito no console.

### Exercícios

[Lista de exercícios - Vetores](https://colab.research.google.com/drive/1C_K-2uDikeSlguChyE10HNMBILl6i1_j)

