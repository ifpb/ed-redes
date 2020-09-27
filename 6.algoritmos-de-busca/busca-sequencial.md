# Busca Sequencial

Buscar dados envolve determinar se um valor \(denominado chave de busca\) está presente no conjunto de dados estudado, e, se estiver, encontrar a localização deste valor.

A forma mais simples e também a mais onerosa é a _**busca exaustiva**_. Nesta técnica, o algoritmo testa cada elemento até encontrar o desejado e, quando alcança o fim do array, informa ao usuário que a chave _não está presente_. Esta pesquisa é geralmente utilizada em arrays desordenados e a parada do algoritmo ocorre apenas quando o elemento é encontrado ou até que todos sejam pesquisados.

{% hint style="info" %}
Na busca exaustiva utilizam- se comandos de repetição \(for, while etc.\) da linguagem para percorrer cada um dos elementos do array. Cada elemento é comparado com o valor pesquisado.
{% endhint %}

Quando dispomos de um conjunto de dados ordenados, podemos utilizar algoritmos de busca mais eficientes, os quais utilizam estratégias que não necessitam percorrer todos os elementos para encontrar o valor pesquisado. Além disso, não é necessário percorrer todos os elementos quando o valor não é encontrado, pois normalmente os algoritmos identificam sua ausência e interrompem o processo.

{% hint style="info" %}
Para utilizarmos um dos algoritmos de pesquisas devemos ter o conjunto dos dados armazenados em um vetor. Não é possível realizar as pesquisas descritas nesta seção utilizando listas interligadas.
{% endhint %}

### Funcionamento da Busca Sequencial

A busca se inicia no primeiro elemento e deve testar os elementos seguintes, devendo continuar até encontrar a chave procurada ou até encontrar o primeiro elemento com valor maior que a chave pesquisada. Como o vetor está ordenado, ao encontrar um elemento maior que a chave procurada, não é necessário continuar verificando, pois, a partir deste elemento, todos os elementos seguintes serão maiores.

Considere o vetor de dados abaixo e a chave de pesquisa **5**. A pesquisa se inicia no primeiro elemento:

![](../.gitbook/assets/image%20%2830%29.png)

Caso não encontre, é verificado o elemento seguinte:

![](../.gitbook/assets/image%20%2832%29.png)

Os elementos seguintes são pesquisados até se encontrar o valor desejado:

![](../.gitbook/assets/image%20%2831%29.png)

Como o valor 5 foi encontrado, o algoritmo retorna a posição em que se encontra o elemento 5 \(no caso, na posição 2\) e interrompe a execução do programa.

Agora considere uma busca na mesma lista pela chave de busca **8**. Os elementos serão visitados até se chegar ao valor 9. Como ele é maior que a chave de busca \(8\), o algoritmo é interrompido. Temos a certeza de que ele não estará no restante do vetor, pois os demais serão, também, maiores que ele.

### Implementação de um algoritmo de busca sequencial

O método abaixo retornará o valor da posição do elemento com o valor pesquisado ou a posição de um elemento com o valor maior. O usuário deverá verificar se a posição retornada possui o valor pesquisado \(encontrou\) ou se possui um valor maior que o pesquisado \(não encontrou\).

O algoritmo “busca\_sequencial” recebe como parâmetro a chave de pesquisa, um vetor a ser buscado e inicia um comando de repetição \(while\) com a condição de parada sendo até percorrer todo o vetor ou até a chave ser maior que o elemento consultado.

Note que caso o elemento exista, é retornada a posição dele no vetor, enquanto que caso ele não exista é retornado o valor **-1**, visto que 0 é uma posição válida da lista.

```text
def busca_sequencial(chave_pesquisa: int, vetor: List[int]):
  for i in range(len(vetor)):
    if vetor[i] == chave_pesquisa:
      return i
    if vetor[i] > chave_pesquisa:
      return -1
  return -1
```

### Versão Recursiva do algoritmo de busca sequencial

```text
def busca_sequencial_recursiva(chave: int, vetor: List[int], i: int = 0):
  if i >= len(vetor) or vetor[i] > chave:
    return -1
  if vetor[i] == chave:
    return i
  return busca_sequencial_recursiva(chave, vetor, i+1) 
```





