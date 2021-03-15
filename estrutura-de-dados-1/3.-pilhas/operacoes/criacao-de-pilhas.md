---
description: 'Estrutura de Dados: Pilha'
---

# Criação de Pilhas

Pilhas são estruturas de dados em que só é possível inserir um novo elemento no final da pilha e só é possível remover um elemento do final da pilha. Dizemos que pilhas seguem um protocolo em que **o último a entrar é o primeiro a sair**. 

Em uma pilha, para que o último elemento a entrar \(ser inserido\) seja o primeiro a sair \(ser removido\), precisamos ser capazes de:

1. Inserir um novo elemento no final da pilha.
2. Remover um elemento do final da pilha.

Uma lista já suporta adicionar um elemento ao final com o método _inserir\_no\_final_ e remover o último elemento com o método _remover\_do\_final_, por isso é natural alinhar o topo da pilha no final da lista, conforme mostrado na Figura a seguir:

![](../../../.gitbook/assets/captura-de-tela-2020-09-13-a-s-13.20.57.png)

Nesta seção mostraremos como implementar uma pilha usando uma estrutura encadeada. Sempre que inserirmos um elemento, o colocaremos no topo da pilha. E sempre que removermos um elemento, removeremos o elemento que está no topo da pilha.

![](../../../.gitbook/assets/image%20%2863%29.png)

No capítulo anterior \(Listas Lineares\), vimos que a lista encadeada possuía uma cabeça, e cada nó da lista encadeada fazia referência ao próximo nó. Nossa pilha funcionará de modo parecido: ela possui um topo, e cada elemento faz referência ao elemento anterior. Essencialmente, as duas implementações são muito parecidas, as únicas mudanças são conceituais \(cabeça vs topo, e próximo vs anterior\), conforme ilustrado na figura acima e mostrado na implementação seguinte.

Para criarmos uma pilha o primeiro passo é criar uma classe Pilha, pois ela é um elemento fundamental dessa nossa explicação:

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

```

Como estamos usando uma estrutura encadeada, é necessário definir a classe No, que será atribuído inicialmente a partir da referência ao `topo` do objeto `Pilha`.

### Verificando se a pilha está vazia

Para verificar se a pilha está vazia, implemente o método `is_empty()`:

```text
class Pilha:
  def __init__(self):
    self.topo = None

  def is_empty(self):
    return self.topo is None
```



