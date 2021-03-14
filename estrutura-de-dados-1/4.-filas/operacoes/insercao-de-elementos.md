---
description: 'Estrutura de Dados: Fila'
---

# Inserção de Elementos

As diferenças entre as filas e pilhas ocorrem na forma como se comportam. As filas de comportam como a Figura a seguir ilustra em relação às suas inserções e remoções

![Inser&#xE7;&#xF5;es e Remo&#xE7;&#xF5;es Fila](../../../.gitbook/assets/image%20%2829%29.png)

## Inserção de Elementos

Em código, para adicionarmos um novo elemento devemos adicionar elementos na lista que foi iniciada na fila. Para isto, criaremos uma função denominada `inserir` que recebe como parâmetro o elemento que precisa ser adicionado à fila. Diferentemente da pilha as filas não tem nomenclaturas padrões para esse métodos.

```text
class Fila:
  def __init__(self, cabeca=None, cauda=None):
    self.cabeca = cabeca
    self.cauda = cauda

  def vazia(self):
    return self.cabeca is None

  def inserir(self, elemento):
    novo_no = No(elemento)

    if self.cabeca == None:
      self.cabeca = self.cauda = novo_no
    else:
      self.cauda.proximo = novo_no
      self.cauda = novo_no
```

Note que a lógica utilizada é a mesma para inserir no final que foi implementada nas listas encadeadas. 

Como faço para testar?

```text
#arquivo fila.py
from fila import Fila

fila_teste = Fila()
fila_teste.inserir("elemento 1")
```

