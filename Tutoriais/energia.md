# Energizando uma entrada

## Aprendendo a ligar e controlar um LED com o @boardname@ @unplugged
![Imagem da Montagem](https://raw.githubusercontent.com/BrinoOficial/TutoriaisMakeCode/master/LEDMicrobit.png)

## {Energizando P0}
Vamos acender o LED.

Arraste um bloco ``||pins:escrever pino P0 para 1||`` para dentro de ``||basic:no iniciar||``.

```blocks
pins.digitalWritePin(DigitalPin.P0, 1)
```

## {Teste}
> Agora ao apertar em ``||Baixar||`` o LED deve acender.

## {Piscar o LED}
Vamos fazer o LED piscar, para isso apague o código anterior.

Dentro de ``||basic:sempre||``:
1. ``||pins:escrever pino P0 para 1||``
2. ``||basic:pausa 500(ms)||``
3. ``||pins:escrever pino P0 para 0||``
4. ``||basic:pausa 500(ms)||``

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P0, 0)
    basic.pause(500)
})
```

## {Teste}
> Agora ao apertar em ``||Baixar||`` o LED deve piscar.
> Ajuste a **pausa** para piscar mais rápido ou mais devagar (100 = rápido, 1000 = lento).

## {Botão liga/desliga}
Vamos controlar o LED com o **botão A**, , para isso apague o código anterior.

Crie a variável ``||variables:ligado||``.

Arraste o bloco ``||input:no botão A pressionado||``

E dentro dele use ``||variables:definir||`` ``||variables:ligado||`` = ``||logic:não||`` ``||variables:ligado||``.

```blocks
let ligado = false
input.onButtonPressed(Button.A, function () {
ligado = !(ligado)
})
```

## {Botão liga/desliga}
Agora vamos adicionar o bloco ``||logic:se, então... senão||`` ainda dentro de ``||input:no botão A pressionado||``.

A condição do  ``||logic:se||`` deve ser a variável ``||variables:ligado||``

```blocks
let ligado = false
input.onButtonPressed(Button.A, function () {
    ligado = !(ligado)
    if (ligado) {   
    } else {
    }
})
```

## {Botão liga/desliga}
No ``||logic:se||`` vamos adicionar ``||pins:gravação digital||`` pin P0 para 1.

No ``||logic:senão||`` vamos fazer a mesma coisa, mas mudar o número para 0

```blocks
let ligado = false
input.onButtonPressed(Button.A, function () {
    ligado = !(ligado)
    if (ligado) {   
        pins.digitalWritePin(DigitalPin.P0, 1)
    } else {
        pins.digitalWritePin(DigitalPin.P0, 0)
    }
})
```

## {Teste}
> Agora ao apertar em ``||Baixar||`` o botão A deve funcionar como uma chave para o LED. 

## {Desafio}
1. **Economia inteligente:** faça o LED apagar sozinho após **10 s** ligado.  