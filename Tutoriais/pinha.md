# Jogo da Pinha

## {Criando Variáveis}
 
Crie as variáveis ``||variables:Sabrina||`` e ``||variables:Pinha||``.

## {Criando Variáveis} 
Dentro de ``||basic:no iniciar||`` use o bloco ``||variables:definir||``:
1. Defina Sabrina para ``||game:criar sprite em x:2 y:4||``
2. Defina Pinha para ``||game:criar sprite em x:0 y:0||``

E ``||variables:Variável||`` para ``||variables:Sabrina||``.


```blocks
let Pinha = game.createSprite(0, 0)
let Sabrina = game.createSprite(2, 4)
```

## {Criando Variáveis}
1. Arraste o bloco ``||math:escolher aleatório||`` para o **x** de onde será criada a ``||variable:Pinha||``.  
2. No bloco ``||math:escolher aleatório||``, mude o segundo número para **4**.  

```blocks
let Pinha = game.createSprite(randint(0, 4), 0)
let Sabrina = game.createSprite(2, 4)
```

## {Movimentação}
1. Adicione o bloco ``||input:no botão B pressionado||``.  
2. Dentro dele, adicione o bloco ``||game:Sabrina mover por 1||``.  
Assim, com **B**, conseguimos nos movimentar para a **direita**.

```blocks
let Sabrina = game.createSprite(2, 4)
input.onButtonPressed(Button.B, function () {
    Sabrina.move(1)
})
```

## {Movimentação}
1. Adicione o bloco ``||input:no botão A pressionado||``.  
2. Dentro dele, adicione o bloco ``||game:Sabrina mover por -1||``.  
Assim, com **A**, conseguimos nos movimentar para a **esquerda**.

```blocks
let Sabrina = game.createSprite(2, 4)
input.onButtonPressed(Button.A, function () {
    Sabrina.move(-1)
})
```

## {Movimentação}
1. Dentro de um bloco ``||basic:sempre||``, adicione o bloco ``||basic:pausa 500(ms)||``.  
2. Logo abaixo, adicione o bloco ``||game:Pinha alterar y por 1||``.

```blocks
let Pinha = game.createSprite(randint(0, 4), 0)
basic.forever(function () {
    basic.pause(500)
    Pinha.change(LedSpriteProperty.Y, 1)
})
```

## {Colisão}

A ``||variables:Sabrina||`` precisa **desviar** das ``||variables:Pinhas||``, para isso:  
1. Dentro do bloco ``||basic:sempre||``, logo abaixo do bloco de ``||game:alterar||``, adicione o bloco ``||logic:se... então||``.  
2. A condição do ``||logic:se||`` deve ser ``||game:is Sabrina touching||``
2. E adicionar o bloco ``||game:fim do jogo||`` no ``||logic:se||``.

```blocks
basic.forever(function () {
    if (Sabrina.isTouching(Pinha)) {
        game.gameOver()
    }
})
```

## {Pontuação}

Vamos aumentar os pontos quando a ``||variables:Pinha||`` chegar na última linha:
1. Dentro de ``||basic:sempre||``, adicione **outro** ``||logic:se||``.  
2. A condição deve ser um **bloco de comparação de igualdade** (``==``) que está em ``||logic:Lógica||``.

```blocks
basic.forever(function () {
    if (0 == 0) {
        
    }
})
```

## {Resetar a Pinha}
1. Troque o primeiro **0** por ``||game:sprite x||``.  
2. Mude **sprite** para ``||variables:Pinha||`` e troque **x** por **y**.  
3. Troque o segundo **0** por **4**.  
Assim o jogo verifica se o **y** da ``||variables:Pinha||`` está na linha **4** (a última).  

```blocks
let Pinha = game.createSprite(randint(0, 4), 0)
basic.forever(function () {
    if (Pinha.get(LedSpriteProperty.Y) == 4) {
        
    }
})
```

## {Pontuação}

Dentro do bloco de ``||logic:se||`` adicione o bloco ``||game:alterar pontuação em||``

```blocks
let Pinha = game.createSprite(randint(0, 4), 0)
basic.forever(function () {
    if (Pinha.get(LedSpriteProperty.Y) == 4) {
        game.addScore(1)
    }
})
```

## {Resetar a Pinha}

Para finalizar, precisamos fazer com que a ``||variables:Pinha||``, ao chegar na última linha, **volte para cima** novamente:
1. Dentro do segundo ``||logic:se||``, adicione um ``||basic:pausa 100(ms)||``.  
2. Use dois blocos ``||game:Pinha definir … para …||``.

- No primeiro, mude para **definir y para 0**.  

- No segundo, mude para **definir x** e coloque um ``||math:escolher aleatório 0 a 4||``.  

```blocks
let Pinha = game.createSprite(randint(0, 4), 0)
basic.forever(function () {
    if (Pinha.get(LedSpriteProperty.Y) == 4) {
        basic.pause(100)
        Pinha.set(LedSpriteProperty.Y, 0)
        Pinha.set(LedSpriteProperty.X, randint(0, 4))
    }
})
```

## {Finalizado}

Primeiro teste o jogo no preview do @boardname no lado esquerdo da tela.

Com o jogo finalizado e funcionando, conecte seu @boardname@ e clique em ``|Baixar|``.

Para aumentar a dificuldade basta diminuir a ``||basic:pausa||`` que fica logo no começo do sempre.
Divirta-se!

```template
basic.forever(function () { })
```
