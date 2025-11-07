# Turbina eólica

## Loop
Primeiro vamos fazer um loop, e dentro dele terá a maioria do nosso código.
Pegue o bloco ``||loop:every 250ms||``

```blocks
loops.everyInterval(250, function () {}
```

## Criando Variáveis
Crie as ``||variables:Variáveis||``:

1. ``||variables:velocidade||``.
2. ``||variables:contador||``.

E inicie elas dentro do nosso loop, defina ``||variables:velocidade||`` para ``||variables:contador||``. E defina ``||variables:contador||`` para 0.

```blocks
loops.everyInterval(250, function () {
  let count = 0
  let speed = count
}
```

## Limpar a tela
Agora vamos usar o bloco ``||basic:limpar tela||`` logo abaixo das definições das variáveis.

```blocks
loops.everyInterval(250, function () {
  let count = 0
  let speed = count
  basic.clearScreen()
}
```

## Mostrar velocidade da turbina
Abaixo do último bloco, vamos criar condições para mostrar o quão rápida está a turbina.

Pegue um bloco ``||logic:se velocidade >= 1 então||``. Dentro dele acenda os leds da primeira linha do micro:bit:
1. ``||led:plotar x 0 y 4||``
2. ``||led:plotar x 1 y 4||``
3. ``||led:plotar x 2 y 4||``
4. ``||led:plotar x 3 y 4||``
5. ``||led:plotar x 4 y 4||``

```blocks
loops.everyInterval(250, function () {
  let count = 0
  let speed = count
  basic.clearScreen()
  if (speed >= 1) {
        led.plot(0, 4)
        led.plot(1, 4)
        led.plot(2, 4)
        led.plot(3, 4)
        led.plot(4, 4)
    }
}
```

## Mostrar velocidade da turbina
Vamos criar a condição para velocidade 2.

Pegue um bloco ``||logic:se velocidade >= 2 então||``. Repita o código da condição anterior substituindo o y por 3:
1. ``||led:plotar x 0 y 3||``
2. ``||led:plotar x 1 y 3||``
3. ``||led:plotar x 2 y 3||``
4. ``||led:plotar x 3 y 3||``
5. ``||led:plotar x 4 y 3||``

```blocks
loops.everyInterval(250, function () {
  let count = 0
  let speed = count
  basic.clearScreen()
  if (speed >= 1) {
        led.plot(0, 4)
        led.plot(1, 4)
        led.plot(2, 4)
        led.plot(3, 4)
        led.plot(4, 4)
    }
  if (speed >= 2) {
        led.plot(0, 3)
        led.plot(1, 3)
        led.plot(2, 3)
        led.plot(3, 3)
        led.plot(4, 3)
    }
}
```

## Mostrar velocidade da turbina
Vamos criar a condição para velocidade 3.

Pegue um bloco ``||logic:se velocidade >= 3 então||``. Repita o código da condição anterior substituindo o y por 2:
1. ``||led:plotar x 0 y 2||``
2. ``||led:plotar x 1 y 2||``
3. ``||led:plotar x 2 y 2||``
4. ``||led:plotar x 3 y 2||``
5. ``||led:plotar x 4 y 2||``

```blocks
loops.everyInterval(250, function () {
  let count = 0
  let speed = count
  basic.clearScreen()
  if (speed >= 1) {
        led.plot(0, 4)
        led.plot(1, 4)
        led.plot(2, 4)
        led.plot(3, 4)
        led.plot(4, 4)
    }
  if (speed >= 2) {
        led.plot(0, 3)
        led.plot(1, 3)
        led.plot(2, 3)
        led.plot(3, 3)
        led.plot(4, 3)
    }
  if (speed >= 3) {
        led.plot(0, 2)
        led.plot(1, 2)
        led.plot(2, 2)
        led.plot(3, 2)
        led.plot(4, 2)
    }
}
```

## Mostrar velocidade da turbina
Vamos criar a condição para velocidade 4.

Pegue um bloco ``||logic:se velocidade >= 4 então||``. Repita o código da condição anterior substituindo o y por 1:
1. ``||led:plotar x 0 y 1||``
2. ``||led:plotar x 1 y 1||``
4. ``||led:plotar x 2 y 1||``
5. ``||led:plotar x 3 y 1||``
6. ``||led:plotar x 4 y 1||``

```blocks
loops.everyInterval(250, function () {
  let count = 0
  let speed = count
  basic.clearScreen()
  if (speed >= 1) {
        led.plot(0, 4)
        led.plot(1, 4)
        led.plot(2, 4)
        led.plot(3, 4)
        led.plot(4, 4)
    }
  if (speed >= 2) {
        led.plot(0, 3)
        led.plot(1, 3)
        led.plot(2, 3)
        led.plot(3, 3)
        led.plot(4, 3)
    }
  if (speed >= 3) {
        led.plot(0, 2)
        led.plot(1, 2)
        led.plot(2, 2)
        led.plot(3, 2)
        led.plot(4, 2)
    }
  if (speed >= 4) {
        led.plot(0, 1)
        led.plot(1, 1)
        led.plot(2, 1)
        led.plot(3, 1)
        led.plot(4, 1)
    }
}
```

## Mostrar velocidade da turbina
Vamos criar a condição para velocidade 5.

Pegue um bloco ``||logic:se velocidade >= 5 então||``. Repita o código da condição anterior substituindo o y por 0:
1. ``||led:plotar x 0 y 0||``
2. ``||led:plotar x 1 y 0||``
4. ``||led:plotar x 2 y 0||``
5. ``||led:plotar x 3 y 0||``
6. ``||led:plotar x 4 y 0||``

```blocks
loops.everyInterval(250, function () {
  let count = 0
  let speed = count
  basic.clearScreen()
  if (speed >= 1) {
        led.plot(0, 4)
        led.plot(1, 4)
        led.plot(2, 4)
        led.plot(3, 4)
        led.plot(4, 4)
    }
  if (speed >= 2) {
        led.plot(0, 3)
        led.plot(1, 3)
        led.plot(2, 3)
        led.plot(3, 3)
        led.plot(4, 3)
    }
  if (speed >= 3) {
        led.plot(0, 2)
        led.plot(1, 2)
        led.plot(2, 2)
        led.plot(3, 2)
        led.plot(4, 2)
    }
  if (speed >= 4) {
        led.plot(0, 1)
        led.plot(1, 1)
        led.plot(2, 1)
        led.plot(3, 1)
        led.plot(4, 1)
    }
  if (speed >= 5) {
        led.plot(0, 0)
        led.plot(1, 0)
        led.plot(2, 0)
        led.plot(3, 0)
        led.plot(4, 0)
    }
}
```

## Pegando contagem de rotações
Para pegar contagem de rotações vamos adicionar o bloco ``||Pins:em pin P1 pulsando alto||``. E dentro dele:
1. ``||variables:alterar contagem por 1||``
2. E tocar um som cada vez que a turbina der um volta com ``||music:play C médio for 1/16 batida in background||``

```blocks
let count = 0
pins.onPulsed(DigitalPin.P1, PulseValue.High, function () {
    count += 1
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Sixteenth)), music.PlaybackMode.InBackground)
})
```

## {Colocando o Còdigo no micro:bit}

Conecte o @boardname@ no computador e clique no botão ``|Download|``.

Agora coloque o micro:bit na turbina eólica e faça o teste.
