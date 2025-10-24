# Receptor de Bits

## {Ler o pino P0}
1. Dentro de ``||basic:sempre||`` adicione um bloco de ``||logic:se ... senão||``.
2. A condição do ``||logic:se||`` deve ser ``||logic:>=||``.
3. o primeiro espaço do ``||logic:>=||`` deve ser ``||pins:leitura analógica pin P0||``, e o segundo 700.

```blocks
basic.forever(function () {
    if (pins.analogReadPin(AnalogPin.P0) >= 700) {
    } else {
    }
})
```

## {Ler o pino P0}
1. No ``||logic:se||`` devemos colocar um bloco ``||basic: mostrar número 0||``
2. No ``||logic:senao||`` devemos limpar a tela com ``||basic:limpar tela||``
```blocks
basic.forever(function () {
    if (pins.analogReadPin(AnalogPin.P0) >= 700) {
        basic.showNumber(0)
    } else {
        basic.clearScreen()
    }
})
```

## {Ler o pino P1}
Para o pino P1 vamos replicar o código anterior, logo abaixo do fim do nosso ``||logic:senão||``.

E a única coisa que vamos mudar é que ao invés de mostrarmos 0 na tela, iremos mostrar o número 1.

```blocks
basic.forever(function () {
    if (pins.analogReadPin(AnalogPin.P0) >= 700) {
        basic.showNumber(0)
    } else {
        basic.clearScreen()
    }
    if (pins.analogReadPin(AnalogPin.P0) >= 700) {
        basic.showNumber(1)
    } else {
        basic.clearScreen()
    }
})
```
---

## {Teste}
1. Carregue este programa no @boardname@ que vai ser o **RECEPTOR**.  
2. Com a montagem igual a descrita no livro podemos testar.  
3. Aperte **A** no emissor para enviar a sequência.  
4. O receptor deve **piscar 0 e 1** a cada **novo** bit.

```template
basic.forever(function () { })
```