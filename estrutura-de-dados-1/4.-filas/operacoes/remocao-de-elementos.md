---
description: 'Estrutura de Dados: Fila'
---

# Remoção de Elementos

Seguindo a lógica de funcionamento apresentada discutida na inserção da filas, daremos continuidade comentando sobre as remoções, que devem acontecer no começo da estrutura \(principal diferencial entre as pilhas\). 

Não é possível remover elementos no meio da fila. Se isso for necessário, é necessário remover os elementos anteriores ao elemento que desejamos remover.  Se isso for feito sem a remoção dos anteriores, você terá implementada qualquer outra coisa, mas não será uma pilha.

## Remoção Padrão

Em código, para remover um elemento da pilha devemos retirá-lo do topo sempre. Para isto, criaremos uma função denominada `remover` que não tem parâmetro, pois ele deve sempre liberar o primeiro elemento da fila que representa o elemento que está armazenado na posição 0.

```text
class Fila:
  def __init__(self, cabeca=None, cauda=None):
    self.cabeca = cabeca
    self.cauda = cauda

  def is_empty(self):
    return self.cabeca is None

  def __repr__(self):
    return "[" + str(self.cabeca) + "]"

  def inserir(self, elemento):
    novo_no = No(elemento)

    if self.cabeca == None:
      self.cabeca = self.cauda = novo_no
    else:
      self.cauda.proximo = novo_no
      self.cauda = novo_no

  def remover(self):
    assert self.cabeca != None, "Impossível remover elemento de fila vazia."
    self.cabeca = self.cabeca.proximo
    if self.cabeca == None:
      self.cauda = None
```

Como testar agora?

```text
class No:
  def __init__(self, carga=0, proximo=None):
    self.carga = carga
    self.proximo = proximo

  def __repr__(self):
    return '%s -> %s' % (self.carga, self.proximo)
        
class Fila:
  def __init__(self, cabeca=None, cauda=None):
    self.cabeca = cabeca
    self.cauda = cauda

  def is_empty(self):
    return self.cabeca is None

  def __repr__(self):
    return "[" + str(self.cabeca) + "]"

  def inserir(self, elemento):
    novo_no = No(elemento)

    if self.cabeca == None:
      self.cabeca = self.cauda = novo_no
    else:
      self.cauda.proximo = novo_no
      self.cauda = novo_no

  def remover(self):
    assert self.cabeca != None, "Impossível remover elemento de fila vazia."
    self.cabeca = self.cabeca.proximo
    if self.cabeca == None:
        self.cauda = None
```

```text
from fila import Fila

def main():
    fila_teste = Fila()
    fila_teste.inserir("elemento1")
    fila_teste.inserir("elemento2")
    fila_teste.inserir("elemento3")
    fila_teste.inserir("elemento4")
    fila_teste.remover()
    fila_teste.removerDado("elemento2")

main()
```

