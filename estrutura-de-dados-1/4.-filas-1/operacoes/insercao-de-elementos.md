---
description: 'Estrutura de Dados: Fila'
---

# Inserção de Elementos

Nossa ... até agora nenhuma diferença! \("Será que a professora não esqueceu de mudar os textos e códigos?" Alguém deve está pensando ... kkkkk\)

As diferenças entre as filas e pilhas ocorrem na forma como se comportam. As filas de comportam como a Figura a seguir ilustra em relação às suas inserções e remoções

![Inser&#xE7;&#xF5;es e Remo&#xE7;&#xF5;es Fila](../../../.gitbook/assets/image%20%2829%29.png)

## Inserção de Elementos

Em código, para adicionarmos um novo elemento devemos adicionar elementos na lista que foi iniciada na fila. Para isto, criaremos uma função denominada **inserirDado** que recebe como parâmetro o elemento que precisa ser adicionado à fila. Diferentemente da pilha as filas não tem nomenclaturas padrões para esse métodos.

```text
class Fila:
    def __init__(self):
        print("__init__")
        self.__dados = []
    
    def is_empty(self):
        return len(self.__dados) == 0

    def inserirDado(self,novoValor):
        self.__dados.append(novoValor)
```

Como faço para testar?

1\) Se usarmos um único .py

```text
class Fila:
    def __init__(self):
        print("__init__")
        self.__dados = []
    
    def is_empty(self):
        return len(self.__dados) == 0

    def inserirDado(self,novoValor):
        self.__dados.append(novoValor)

def main():
    fila_teste = Fila()
    fila_teste.inserirDado("elemento 1")

main()
```

2\) Para arquivos .py diferentes é a mesma lógica, mas você precisa importar a classe Pilha antes de utilizá-la.

```text
#fila.py
class Fila:
    def __init__(self):
        print("__init__")
        self.__dados = []
    
    def is_empty(self):
        return len(self.__dados) == 0

    def inserirDado(self,novoValor):
        self.__dados.append(novoValor)
```

```text
#arquivo teste.py
from fila import Fila

fila_teste = Fila()
fila_teste.inserirDado("elemento 1")
```

