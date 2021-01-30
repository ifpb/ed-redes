# Execução do Algoritmo de Fibonacci Recursivo

Vamos considerar como exemplo a implementação do algoritmo de Fibonacci de maneira recursiva:

```text
def fibonacci(n: int) -> int:
  if n <= 1:
    return n
  else:
    return fibonacci(n-1) + fibonacci(n-2)

print(fibonacci(5))
```

A memória no computador possui um endereço e um valor. Para fins didáticos, vamos supor que esta memória seja sequencial, iniciando no endereço 0x01 e que possui uma etiqueta, referente ao nome da variável:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/Qk2lt.png)

O programa irá executar a última linha do código, reservando um espaço na memória para a variável e definido o retorno da função como sendo seu valor:

```text
resultado = fibonacci(5)
```

Na memória fica:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/gdgaw.png)

### Passo 1

Para saber qual valor de `fibonacci(5)`, a função `fibonacci` é executada:

1. A função `fibonacci` é chamada com parâmetro `n = 5`;
2. Verifica-se se `n` é menor ou igual a 1. Falso, executa o `else`;
3. Retorne o valor de `fibonacci(4) + fibonacci(3)`;

Ou seja, o valor de `fibonacci(5)` será `fibonacci(4) + fibonacci(3)`. Então na memória, ficaria:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/33d5D.png)

### Passo 2

Então, o programa irá tentar primeiro calcular o valor de `fibonacci(4)`, pois a expressão é analisada da esquerda para a direita:

1. A função `fibonacci` é chamada com parâmetro `n = 4`;
2. Verifica-se se `n` é menor ou igual a 1. Falso, executa o `else`;
3. Retorne o valor de `fibonacci(3) + fibonacci(2)`;

Ou seja, o valor de `fibonacci(4)` será `fibonacci(3) + fibonacci(2)`. Então na memória, ficaria:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/X4RQS.png)

### Passo 3

Então, para saber o valor de `fibonacci(4)`, o programa precisa saber o valor de `fibonacci(3)` e `fibonacci(2)`. Analisando da esquerda para a direita, primeiro é calculado `fibonacci(3)`:

1. A função `fibonacci` é chamada com parâmetro `n = 3`;
2. Verifica-se se `n` é menor ou igual a 1. Falso, executa o `else`;
3. Retorne o valor de `fibonacci(2) + fibonacci(1)`;

Ou seja, o valor de `fibonacci(3)` será `fibonacci(2) + fibonacci(1)`. Então na memória, ficaria:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/nR4Mp.png)

### Passo 4

A mesma lógica: para saber o valor de `fibonacci(3)`, antes é necessário saber o valor de `fibonacci(2)` e `fibonacci(1)`. Da esquerda para a direita, calcula-se o valor de `fibonacci(2)`:

1. A função `fibonacci` é chamada com parâmetro `n = 2`;
2. Verifica-se se `n` é menor ou igual a 1. Falso, executa o `else`;
3. Retorne o valor de `fibonacci(1) + fibonacci(0)`;

Ou seja, o valor de `fibonacci(2)` será `fibonacci(1) + fibonacci(0)`. Então na memória, ficaria:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/U67z9.png)

### Passo 5

Para calcular o valor de `fibonacci(2)` então é preciso de `fibonacci(1)` e `fibonacci(0)`. Da esquerda para a direita, calcula-se primeiro `fibonacci(1)`:

1. A função `fibonacci` é chamada com parâmetro `n = 1`;
2. Verifica-se se `n` é menor ou igual a 1. Verdadeiro;
3. Retorne o valor de `n` \(1\);

Neste ponto, a recursividade é interrompida brevemente, pois o valor não depende mais de uma outra chamada da função. Assim, na memória fica:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/U2GIP.png)

### Passo 6

Assim, tendo o valor de `fibonacci(1)`, este é substituído em `fibonacci(2)`:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/mGuHF.png)

### Passo 7

Mas ainda é necessário calcular o valor de `fibonacci(0)`:

1. A função `fibonacci` é chamada com parâmetro `n = 0`;
2. Verifica-se se `n` é menor ou igual a 1. Verdadeiro;
3. Retorne o valor de `n` \(0\);

Então na memória fica:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/2bFZq.png)

### Passo 8

Este valor é prontamente substituído no valor de `fibonacci(2)`:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/tPbSk.png)

### Passo 9

O valor de `fibonacci(2)` é obtido somando 1+0 = 1 e é substituído em `fibonacci(3)`:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/6t93c.png)

### Passo 10

Para calcular o valor final de `fibonacci(3)` é preciso o valor de `fibonacci(1)` novamente, então é feito novamente a chamada:

1. A função `fibonacci` é chamada com parâmetro `n = 1`;
2. Verifica-se se `n` é menor ou igual a 1. Verdadeiro;
3. Retorne o valor de `n` \(1\);

Ficando na memória:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/uIo20.png)

### Passo 11

Este valor é prontamente substituído em `fibonacci(3)`, ficando:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/8Er4X.png)

### Passo 12

O valor de `fibonacci(3)` então valerá 1+1 = 2, sendo substituído em `fibonacci(4)`:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/sYt50.png)

### Passo 13

Mas novamente é preciso o valor de `fibonacci(2)`, então:

1. A função `fibonacci` é chamada com parâmetro `n = 2`;
2. Verifica-se se `n` é menor ou igual a 1. Falso, executa o `else`;
3. Retorne o valor de `fibonacci(1) + fibonacci(0)`;

Ficando na memória:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/8q1Sh.png)

### Passo 14

Já sabemos que `fibonacci(1)` retornará 1 e `fibonacci(0)` retornará 0, então para simplificar, colocarei direto seus valores em `fibonacci(2)`:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/KLyHm.png)

### Passo 15

Ficando o valor de `fibonacci(2)` igual a 1+0 = 1, sendo prontamente substituído em `fibonacci(4)`:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/2AsFi.png)

### Passo 16

Assim, o valor de `fibonacci(4)` ficará igual à 2+1 = 3, sendo prontamente substituído em `fibonacci(5)`:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/157pw.png)

### Passo 17

Para calcular ainda o valor final de `fibonacci(5)` é necessário o valor de `fibonacci(3)`:

1. A função `fibonacci` é chamada com parâmetro `n = 3`;
2. Verifica-se se `n` é menor ou igual a 1. Falso, executa o `else`;
3. Retorne o valor de `fibonacci(2) + fibonacci(1)`;

Ou seja, o valor de `fibonacci(3)` será `fibonacci(2) + fibonacci(1)`:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/wAdjm.png)

### Passo 18

Analisando da esquerda para a direita, novamente calcula-se o valor de `fibonacci(2)`:

1. A função `fibonacci` é chamada com parâmetro `n = 2`;
2. Verifica-se se `n` é menor ou igual a 1. Falso, executa o `else`;
3. Retorne o valor de `fibonacci(1) + fibonacci(0)`;

Ficando na memória:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/xonSt.png)

### Passo 19

Como já sabemos, `fibonacci(1)` vale 1 e `fibonacci(0)` vale 0, então substituindo os valores:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/xChbo.png)

### Passo 20

Resultando em `fibonacci(2)` igual a 1+0 = 1, sendo prontamente substituído em `fibonacci(3)`:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/e2Zsd.png)

### Passo 21

Falta ainda calcular o valor de `fibonacci(1)`, que já sabemos que vale 1:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/KJcLw.png)

### Passo 22

Assim, o valor de `fibonacci(3)` será 1+1 = 2, sendo prontamente substituído em `fibonacci(5)`:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/ujhXT.png)

### Passo 23

Finalmente, o valor de `fibonacci(5)` valerá 3+2 = 5, sendo substituído prontamente em `resultado`:

![inserir a descri&#xE7;&#xE3;o da imagem aqui](https://i.stack.imgur.com/YY2dp.png)

Portanto, quando for executado:

```text
resultado = fibonacci(5)
```

O valor de `resultado` será 5. Valor este que pode ser comprovado executando o código.

>

