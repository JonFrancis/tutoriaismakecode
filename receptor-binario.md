# Receptor de Bits

## Vamos agora ler os sinais enviados pelo nosso emissor para descobrir a mensagem

---

## {Ler o pino P0}
Dentro de ``||basic:sempre||`` adicione um bloco de ``||logic:Lógica||`` ``||logic:se ... senão||``.

```blocks
basic.forever(function () {
    if (true) {
    } else {
    }
})
```
---
## {Ler o pino P0}
Nossa condição vai ser uma condição de lógica ``||logic:>=||``, maior ou igual.
- ``||pins:leitura analógica pin P0||`` >= 700

```blocks
basic.forever(function () {
    if (pins.analogReadPin(AnalogPin.P0) >= 700) {
    } else {
    }
})
```
---
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