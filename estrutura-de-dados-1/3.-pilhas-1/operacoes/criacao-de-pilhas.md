---
description: 'Estrutura de Dados: Pilha'
---

# Criação de Pilhas

Pilhas são estruturas de dados em que só é possível inserir um novo elemento no final da pilha e só é possível remover um elemento do final da pilha. Dizemos que pilhas seguem um protocolo em que **o último a entrar é o primeiro a sair**. Pilhas são geralmente implementadas com arranjos.

Em uma pilha, para que o último elemento a entrar \(ser inserido\) seja o primeiro a sair \(ser removido\), precisamos ser capazes de:

1. Inserir um novo elemento no final da pilha.
2. Remover um elemento do final da pilha.

facilidade, armazenando seus elementos em uma lista Python. 

Uma lista já suporta adicionar um elemento ao final com o método _inserir\_no\_final_ e remover o último elemento com o método _remover\_do\_final_, por isso é natural alinhar o topo da pilha no final da lista, conforme mostrado na Figura a seguir:

![](../../../.gitbook/assets/captura-de-tela-2020-09-13-a-s-13.20.57.png)

Para criarmos uma pilha o primeiro passo é criar uma classe Pilha, pois ela é um elemento fundamental dessa nossa explicação:

```text
class No:
    def __init__(self, carga=0, proximo=None):
        self.carga = carga
        self.proximo = proximo

    def __repr__(self):
        return '%s -> %s' % (self.dado, self.proximo)
        
class Pilha:
    def __init__(self):
        self.topo = None

    def __repr__(self):
        return "[" + str(self.topo) + "]"

```

### Verificando se a pilha está vazia

Para verificar se a pilha está vazia, implemente o método is\_empty\(\):

```text
class Pilha:
    def __init__(self):
        self.topo = None   
        
    #retorna True se for vazia
    def is_empty(self):
      return self.cabeca == None
```



