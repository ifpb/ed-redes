---
description: 'Estrutura de Dados: Pilha'
---

# Impressão, topo e tamanho da pilha

Estamos adicionando e removendo elementos, mas ainda não conseguimos acompanhar o crescimento e o topo da pilha.

Como tais funções devem ser implementadas. Neste caso, não há nomes fixos para esses métodos \(como o PUSH e POP\), mas eles devem ter nomes claros sobre isso.

Para imprimir a pilha, basta implementar o método \_\_str\_\_ \(em alguns casos observamos o método getPilha também, mas entenderemos melhor a seguir\)

```text
class Pilha:
    def __init__(self):
        self.__dados = []

    #retorna True se for vazia
    def is_empty(self):
      return len(self.__dados) == 0

    def push(self, novoElem):
        self.__dados.append(novoElem)

    def pop(self):
        if self.is_empty():
            return "Lista Vazia - Não houve Remoção"
        return self.__dados.pop()

    def __str__(self):
        return str(self.__dados)
```

## Verificar o topo da pilha

Outra operação importante, é a verificação do topo da pilha. Faremos isso por meio do método topo:

```text
 def topo(self):
        if self.is_empty():
          return ("Pilha vazia")
        else: 
          return self.__dados[−1]
```

```text
class Pilha:
    def __init__(self):
        self.__dados = []

    #retorna True se for vazia
    def is_empty(self):
      return len(self.__dados) == 0

    def push(self, novoElem):
        self.__dados.append(novoElem)

    def pop(self):
        if self.is_empty():
            return "Lista Vazia - Não houve Remoção"
        return self.__dados.pop()

    def __str__(self):
        return str(self.__dados)
        
    def topo(self):
        if self.is_empty():
          return ("Pilha vazia")
        else: 
          return self.__dados[−1]
```

## Tamanho da pilha

Por fim, uma última operação importante é a de verificação do tamanho da pilha. Faremos isso com o auxílio da função len das listas em Python.

```text
 def __len__(self): 
      return len(self.__dados)
```

E nossa classe Pilha ficará assim:

```text
class Pilha:
    def __init__(self):
        self.__dados = []

    #retorna True se for vazia
    def is_empty(self):
      return len(self.__dados) == 0

    def push(self, novoElem):
        self.__dados.append(novoElem)

    def pop(self):
        if self.is_empty():
            return "Lista Vazia - Não houve Remoção"
        return self.__dados.pop()

    def __str__(self):
        return str(self.__dados)
        
    def topo(self):
        if self.is_empty():
          return ("Pilha vazia")
        else: 
          return self.__dados[−1]
          
    def __len__(self): 
      return len(self.__dados)
```

