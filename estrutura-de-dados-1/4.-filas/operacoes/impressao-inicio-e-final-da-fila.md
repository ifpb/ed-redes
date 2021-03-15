---
description: 'Estrutura de Dados: Fila'
---

# Impressão, inicio e final da fila

Contudo, novamente, estamos adicionando e removendo elementos, mas ainda não conseguimos acompanhar o crescimento da fila.

Como tais funções devem ser implementadas. Neste caso, não há nomes fixos para esses métodos, mas eles devem ter nomes claros sobre isso.

Para imprimir a fila, basta implementar o método `__repr__`\(método recomendado para exibir informações dos objetos\)

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

## Início e final da fila

Outra operação importante, é a verificação do início da fila. Para isto, basta acessar os atributos `cabeca` e `cauda` da fila.

## Tamanho da fila

Por fim, um método para verificar o tamanho da estrutura. Para imprimir o tamanho, basta executar `print(len(fila))`

```text
class Fila:
  def __init__(self, cabeca=None, cauda=None):
    self.cabeca = cabeca
    self.cauda = cauda

  def __len__(self):
    atual = self.cabeca
    total = 0
    while atual is not None:
      total += 1
      atual = atual.proximo
    return total
```

