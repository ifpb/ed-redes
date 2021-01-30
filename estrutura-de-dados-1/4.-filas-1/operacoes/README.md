---
description: 'Estrutura de Dados: Fila'
---

# Operações

Há três abordagens possíveis para implementar filas: \(i\) com base em um vetor, \(ii\) usando uma lista encadeada, e \(iii\) usando uma matriz circular. Nós discutiremos com base em um vetor. 

Anteriormente, foi discutido como implementar uma pilha usando vetores como a base da estrutura. Nesta seção, será discutido a implementação de uma fila usando uma estrutura semelhante. 

Em nossa implementação de pilha, tanto inserções quanto remoções ocorriam no final da pilha. Em filas, inserções ocorrem no final e remoções ocorrem no começo. Para isso, usaremos dois ponteiros \(interprete como variáveis\): um para o começo da fila, e outro para o final. Esses ponteiros nos permitirão implementar inserções e remoções com custo constante. 

 Uma etapa fundamental para entender tal estrutura é explorar as operações principais da mesma. Entre elas destacaremos:

* Criação de uma fila;
* Verificar se fila está vazia;
* Inserção de elementos em uma fila;
* Remoção de elementos em uma fila;
* Impressão dos valores da fila;
* Verificar inicio da fila,
* Tamanho da fila.

