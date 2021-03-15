---
description: 'Estrutura de Dados: Pilha'
---

# Impressão, topo e tamanho da pilha

Estamos adicionando e removendo elementos, mas ainda não conseguimos acompanhar o crescimento e o topo da pilha.

Como tais funções devem ser implementadas. Neste caso, não há nomes fixos para esses métodos \(como o PUSH e POP\), mas eles devem ter nomes claros sobre isso.

Para imprimir a pilha, basta implementar o método `__repr__` \(recomendado para imprimir detalhes de um objeto\).

```text
class No:
  def __init__(self, carga=0, anterior=None):
    self.carga = carga
    self.anterior = anterior

  def __repr__(self):
    return '%s -> %s' % (self.carga, self.anterior)

class Pilha:
  def __init__(self):
    self.topo = None

  def is_empty(self):
    return self.topo is None

  def push(self, elemento):
    no = No(elemento)
    no.anterior = self.topo
    self.topo = no

  def pop(self):
    assert self.topo != None, "Impossível remover elemento de pilha vazia."
    self.topo = self.topo.anterior

  def __repr__(self):
    return "[" + str(self.topo) + "]"
```

## Verificar o topo da pilha

Outra operação importante, é a verificação do topo da pilha. Para isso basta acessar o atributo `topo` do objeto pilha.

## Tamanho da Pilha

Por fim, outra operação importante é a de verificação do tamanho da pilha. Faremos definindo um método `__len__` para a nossa estrutura encadeada.

```text
  def __len__(self):
    atual = self.topo
    c = 0
    while atual is not None:
      c += 1
      atual = atual.anterior
    return c
```

E nossa classe Pilha ficará assim:

```text
class Pilha:
  def __init__(self):
    self.topo = None

  def is_empty(self):
    return self.topo is None

  def push(self, elemento):
    no = No(elemento)
    no.anterior = self.topo
    self.topo = no

  def pop(self):
    assert self.topo != None, "Impossível remover elemento de pilha vazia."
    self.topo = self.topo.anterior

  def __repr__(self):
    return "[" + str(self.topo) + "]"

  def __len__(self):
    atual = self.topo
    c = 0
    while atual is not None:
      c += 1
      atual = atual.anterior
    return c
```

