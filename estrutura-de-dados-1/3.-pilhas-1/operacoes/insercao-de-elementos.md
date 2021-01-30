---
description: 'Estrutura de Dados: Pilha'
---

# Inserção de elementos

Inicialmente, é importante entender o funcionamento de uma pilha.

A Figura a seguir ilustra como deve ser o armazenamento dos novos dados em uma pilha. Percebam que todo novo elemento inserido \(pode ser de qualquer tipo de dado\) é SEMPRE adicionado no topo da estrutura, assim como fazemos com as moedas mencionadas no começo dessa conversa \(Como estamos trabalhando com lista o topo representa o final da lista\).

![Inser&#xE7;&#xE3;o Pilha](../../../.gitbook/assets/captura-de-tela-2020-09-13-a-s-13.46.32.png)

Em código, para adicionarmos um novo elemento devemos adicionar elementos na lista que foi inicializada na pilha. Para isto, criaremos uma função denominada PUSH que recebe como parâmetro o elemento que precisa ser adicionado à pilha. 

```text
class Pilha:
    def __init__(self):
        self.__dados = []

    #retorna True se for vazia
    def is_empty(self):
      return len(self.__dados) == 0
      
    def push(self, novoElem): 
        self.__dados.append(novoElem)
```

Como devemos testar?

1\) Se usarmos um único .py

```text
class Pilha:
    def __init__(self):
        self.__dados = []
        
    #retorna True se for vazia
    def is_empty(self):
      return len(self.__dados) == 0
    
    def push(self, novoElem): 
        self.__dados.append(novoElem)

def main():
    pilhaTeste = Pilha()
    pilha.push("elemento 1)

main()
```

2\) Para arquivos .py diferentes é a mesma lógica, mas você precisa importar a classe Pilha antes de utilizá-la.

```text
#pilha.py

class Pilha:
    def __init__(self):
        self.__dados = []
        
    #retorna True se for vazia
    def is_empty(self):
      return len(self.__dados) == 0
    
    def push(self, novoElem): 
        self.__dados.append(novoElem)
```

```text
#teste.py

from pilha import Pilha 

def main():
    pilhaTeste = Pilha()
    pilha.push("elemento 1)

main()
```



