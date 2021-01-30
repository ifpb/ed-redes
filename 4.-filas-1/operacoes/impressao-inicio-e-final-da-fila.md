---
description: 'Estrutura de Dados: Fila'
---

# Impressão, inicio e final da fila

Contudo, novamente, estamos adicionando e removendo elementos, mas ainda não conseguimos acompanhar o crescimento da fila.

Como tais funções devem ser implementadas. Neste caso, não há nomes fixos para esses métodos, mas eles devem ter nomes claros sobre isso.

Para imprimir a fila, basta implementar o método \_\_str\_\_ \(em alguns casos observamos o método getFila também, mas entenderemos melhor a seguir\)

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
            
    def __str__(self):
        return str(self.__dados)
```

## Início e final da fila

Outra operação importante, é a verificação do início da fila. Faremos isso por meio dos métodos **inicio** e **final**:

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

    def inicio(self):
      if self.is_empty():
        return ("Fila vazia")
      else: 
        return self.__dados[0]

    def final(self):
      if self.is_empty():
        return ("Fila vazia")
      else: 
        return self.__dados[-1]

    def __str__(self):
        return str(self.__dados)
```

## Tamanho da fila

Por fim, um método para verificar o tamanho da estrutura:

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

    def inicio(self):
      if self.is_empty():
        return ("Fila vazia")
      else: 
        return self.__dados[0]

    def final(self):
      if self.is_empty():
        return ("Fila vazia")
      else: 
        return self.__dados[-1]

    def __str__(self):
        return str(self.__dados)

    def __len__(self):
        return len(self.__dados)
```

