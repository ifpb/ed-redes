---
description: 'Estrutura de Dados: Fila'
---

# Remoção de Elementos

Seguindo a lógica de funcionamento apresentada discutida na inserção da filas, daremos continuidade comentando sobre as remoções, que devem acontecer no começo da estrutura \(principal diferencial entre as pilhas\). 

Não é possível remover elementos no meio da fila. Se isso for necessário, é necessário remover os elementos anteriores ao elemento que desejamos remover.  Se isso for feito sem a remoção dos anteriores, você terá implementada qualquer outra coisa, mas não será uma pilha.

## Remoção Padrão

Em código, para remover um elemento da pilha devemos retirá-lo do topo sempre. Para isto, criaremos uma função denominada **remover** que não tem parâmetro, pois ele deve sempre liberar o primeiro elemento da fila que representa o elemento que está armazenado na posição 0.

```text
class Fila:
    def __init__(self):
        print("__init__")
        self.__dados = []
    
    def is_empty(self):
        return len(self.__dados) == 0

    def inserirDado(self,novoValor):
        self.__dados.append(novoValor)

    def remover(self):
        self.__dados.pop(0)
```

## Remoção de um elemento específico

Imagina agora que você precisa remover um elemento especificamente da sua fila. Para isto, você só precisa ter remover os elementos antes e tal tarefa foi implementada no método **removerDado**

```text
class Fila:
    def __init__(self):
        print("__init__")
        self.__dados = []
    
    def is_empty(self):
        return len(self.__dados) == 0

    def inserirDado(self,novoValor):
        self.__dados.append(novoValor)

    def remover(self):
        self.__dados.pop(0)

    def removerDado(self,valor):
        pos = self.__dados.index(valor)
        for i in range(0,pos+1):
            self.__dados.pop(0)
```

Como testar agora?

1\) No mesmo .py

```text
class Fila:
    def __init__(self):
        print("__init__")
        self.__dados = []
    
    def is_empty(self):
        return len(self.__dados) == 0

    def inserirDado(self,novoValor):
        self.__dados.append(novoValor)

    def remover(self):
        self.__dados.pop(0)

    def removerDado(self,valor):
        pos = self.__dados.index(valor)
        for i in range(0,pos+1):
            self.__dados.pop(0)

def main():
    fila_teste = Fila()
    fila_teste.inserirDado("elemento1")
    fila_teste.inserirDado("elemento2")
    fila_teste.inserirDado("elemento3")
    fila_teste.inserirDado("elemento4")
    fila_teste.remover()
    fila_teste.removerDado("elemento2")

main()
```

2\) Utilizando dois arquivos .py

```text
class Fila:
    def __init__(self):
        print("__init__")
        self.__dados = []
    
    def is_empty(self):
        return len(self.__dados) == 0

    def inserirDado(self,novoValor):
        self.__dados.append(novoValor)

    def remover(self):
        self.__dados.pop(0)

    def removerDado(self,valor):
        pos = self.__dados.index(valor)
        for i in range(0,pos+1):
            self.__dados.pop(0)
```

```text
from fila import Fila

def main():
    fila_teste = Fila()
    fila_teste.inserirDado("elemento1")
    fila_teste.inserirDado("elemento2")
    fila_teste.inserirDado("elemento3")
    fila_teste.inserirDado("elemento4")
    fila_teste.remover()
    fila_teste.removerDado("elemento2")

main()
```

