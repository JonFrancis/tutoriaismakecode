```package
github:YahboomTechnology/Superbit-expansion-board
```
# Centrífuga

## Vamos ligar a cetrífuga

Vamos fazer a centrífuga começar a funcionar quando apertarmos o botão A.
1. Vamos adicionar o bloco ``||input:no botão A pressionado||``
2. Dentro dele acionar o motor com ``||SuperBit:Motor M1 speed 255||``

```blocks
input.onButtonPressed(Button.A, function () {
    SuperBit.MotorRun(SuperBit.enMotors.M1, 255)
})
```

## Vamos desligar a cetrífuga

Vamos fazer a centrífuga começar a funcionar quando apertarmos o botão A.
1. Vamos adicionar o bloco ``||input:no botão B pressionado||``
2. Dentro dele acionar o motor com ``||SuperBit:Motor M1 speed 0||``

```blocks
input.onButtonPressed(Button.B, function () {
    SuperBit.MotorRun(SuperBit.enMotors.M1, 0)
})
```

## {Colocando o Còdigo no micro:bit}

Conecte o @boardname@ no computador e clique no botão ``|Download|``.

Agora coloque o micro:bit na nossa centrífuga e faça o teste


```template
SuperBit.MotorStopAll()
basic.forever(function () {
	
})
```