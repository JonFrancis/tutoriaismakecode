# Jogo dos Reflexos

## Introdução

*Jogo dos Reflexos* é um jogo de habilidade em que o jogador precisa pressionar **A** exatamente quando o ponto chega ao centro da tela.

## Crie uma variável

Na aba ``||variables:Variáveis||`` crie uma nova variável e chame ela de `ponto`.
Crie um bloco ``||basic:Básico||`` ``||basic:no iniciar||``.
Arraste um bloco ``||variables:definir sprite para||`` para dentro do ``||basic:no iniciar||`` e troque ``sprite`` para ``||variables:ponto||``.

```blocks
let ponto = 0
```

## Crie um sprite

Em ``||advanced:Avançado||`` puxe um bloco de ``||game:Jogo||`` ``||game:criar sprite||`` e coloque-o dentro de ``||variables:deinir sprite para||`` substituindo o `0`. 
O *ponto* é um único pixel que pode se mover na tela. 
Ele possui uma posição ``x`` e ``y`` junto com uma direção de movimento.

```blocks
let ponto = game.createSprite(2, 2)
```

## Mova o ponto

O ``||variables:ponto||`` começa no centro apontando para a direita. 
Coloque um bloco ``||game:mover||`` dentro de ``||basic:sempre||`` para fazê-lo se mover. 
Note que ele se move para a direita, mas não volta.

```blocks
let Ponto = game.createSprite(2, 2)
basic.forever(function () {
    Ponto.move(1)
})
```

## Fazer o ponto sair do canto

Pegue um bloco de ``||game:Jogo||`` ``||game:se na borda, saltar||`` para fazer o ``||variables:ponto||`` quicar na borda da tela. 
Também adicione um bloco ``||basic:pause||`` para que ele não se mova muito rápido.

```blocks
let ponto = game.createSprite(2, 2)
basic.forever(function () {
    ponto.move(1)
    ponto.ifOnEdgeBounce()
    basic.pause(100)
})
```

## Utilizando os Reflexos

Quando **A** for pressionado, testamos se o ``||variables:ponto||`` está no centro ou não.
Use um bloco de ``||input:Entrada||`` ``||input:no botão pressionado||`` para tratar o botão **A**. 
Coloque um bloco ``||logic:se ... senão||``.

```blocks
let ponto = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
    if (true) {
    } else {
    }
})
basic.forever(function () {
    ponto.move(1)
    basic.pause(100)
    ponto.ifOnEdgeBounce()
})
```

## Utilizando os Reflexos

Dentro de verdadeiro use um bloco de comparação de igualdade que você encontra em ``||logic:Lógica||``.
Para o primeiro espaço da comparação pegue x do ``||variables:ponto||`` na aba de ``||game:Jogo||`` e coloque `2` no segundo espaço.

```blocks
let ponto = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
    if (ponto.get(LedSpriteProperty.X) == 2) {
    } else {
    }
})
basic.forever(function () {
    ponto.move(1)
    basic.pause(100)
    ponto.ifOnEdgeBounce()
})
```

## Pontuação e fim de jogo

Por fim, puxe um bloco ``||game:alterar pontuação||`` e um bloco ``||game:fim de jogo||`` para lidar tanto com o sucesso (sprite no centro) quanto com a falha (sprite fora do centro).

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

## Teste e faça o download

Seu jogo está pronto! Conecte seu @boardname@, pressione ``|Baixar|`` para experimentá-lo no dispositivo.