# Jogo dos Reflexos

## {Variável}
1. Crie uma variável e chame ela de ``||variables:ponto||``.
2. Arraste um bloco ``||variables:definir ponto para||`` para dentro de ``||basic:no iniciar||``.
3. Pegue o bloco ``||game:criar sprite||`` e coloque-o dentro de ``||variables:deinir sprite para||`` substituindo o **0**. 

```blocks
let ponto = game.createSprite(2, 2)
```

## {Movimentação}
1. Coloque um bloco ``||game:mover||`` dentro de ``||basic:sempre||``. 
Assim nosso ``||variables:ponto||`` se move para a direita.

```blocks
let Ponto = game.createSprite(2, 2)
basic.forever(function () {
    Ponto.move(1)
})
```

## {Movimentação}
1. Arraste o bloco de ``||game:se na borda, saltar||`` para fazer o ``||variables:ponto||`` quicar na borda da tela. 
2. Também adicione um bloco ``||basic:pause||`` para que ele não se mova muito rápido.

```blocks
let ponto = game.createSprite(2, 2)
basic.forever(function () {
    ponto.move(1)
    ponto.ifOnEdgeBounce()
    basic.pause(100)
})
```

## {Reflexos}
Quando **A** for pressionado, testamos se o ``||variables:ponto||`` está no centro ou não:

1. Use o ``||input:no botão A pressionado||``. 
2. Coloque um bloco ``||logic:se ... senão||`` dentro dele.

```blocks
let ponto = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
    if (true) {
    } else {
    }
})
```

## {Reflexos}
1. A condição do ``||logic:se||`` deve ser ``||logic:=||``
2. O primeiro espaço de ``||logic:=||`` deve ser ``||game:ponto x||``
3. O segundo espaço de ``||logic:=||`` deve ser **2**

```blocks
let ponto = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
    if (ponto.get(LedSpriteProperty.X) == 2) {
    } else {
    }
})
```

## {Pontuação}

Por fim:
1. No ``||logic:se||`` devemos ter um bloco ``||game:alterar pontuação||``
2. No ``||logic:senão||`` devemos ter um bloco ``||game:fim de jogo||``

```blocks
let ponto = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
    if (ponto.get(LedSpriteProperty.X) == 2) {
        game.addScore(1)
    } else {
        game.gameOver()
    }
})
basic.forever(function () {
    ponto.move(1)
    basic.pause(100)
    ponto.ifOnEdgeBounce()
})
```

## {Finalizado}

Primeiro teste o jogo no preview do @boardname no lado esquerdo da tela.

Com o jogo finalizado e funcionando, conecte seu @boardname@ e clique em ``|Baixar|``.

Divirta-se!