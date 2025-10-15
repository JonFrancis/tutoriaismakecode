# Receptor de Bits

## Vamos agora ler os sinais enviados pelo nosso emissor para descobrir a mensagem

## {Variável de controle}
Crie a variável ``||variables:lendo||``. Ela evita contar o **mesmo bit** mais de uma vez.

No bloco ``||basic:no iniciar||``, deixe ``||variables:lendo||`` como **falso**.

```blocks
let lendo = false
```

---

## {Ler os pinos P0 e P1}
Vamos criar duas variáveis para guardar a leitura dos pinos a cada instante: ``||variables:b0||`` e ``||variables:b1||``.

No bloco ``||basic:sempre||``:
- Defina ``||variables:b0||`` = ``||pins:leitura digital pin P0||``
- Defina ``||variables:b1||`` = ``||pins:leitura digital pin P1||``

```blocks
let b0 = 0
let b1 = 0
basic.forever(function () {
    b0 = pins.digitalReadPin(DigitalPin.P0)
    b1 = pins.digitalReadPin(DigitalPin.P1)
})
```

---

## {Detectar o novo bit}
Ainda dentro do ``||basic:sempre||``, crie um bloco ``||logic:se...senão se||``.
E dentro dele um bloco  ``||logic:se... senão se ...||``
```blocks
let lendo = false
let b0 = 0
let b1 = 0
basic.forever(function () {
    b0 = pins.digitalReadPin(DigitalPin.P0)
    b1 = pins.digitalReadPin(DigitalPin.P1)
    if (true) {
        if (true) {
            
        } else if (true) {
            
        }
    } else {

    }
})
```
---

## {Detectar o novo bit}
Dentro do primeiro bloco ``||logic:se||`` a condição vai ser ``lendo = falso``.

Dentro do segundo bloco ``||logic:se||`` a condição vai ser ``b0 = 1`` **e** ``b1 = 0``.

Dentro do primeiro bloco ``||logic:senão||`` a condição vai ser ``b1 = 1`` **e** ``b0 = 0``.

E dentro do segundo bloco ``||logic:senão||`` a condição vai ser ``b1 = 0`` **e** ``b0 = 0``.
```blocks
let lendo = false
let b0 = 0
let b1 = 0
basic.forever(function () {
    b0 = pins.digitalReadPin(DigitalPin.P0)
    b1 = pins.digitalReadPin(DigitalPin.P1)
    if ((!(lendo)) {
        if (b0 == 1 && b1 == 0) {
            
        } else if (b1 == 1 && b0 == 0) {
            
        }
    } else if (b1 == 0 && b0 == 0) {

    }
})
```

---
## {Detectar o novo bit}
Dentro do segundo bloco ``||logic:se||`` vamos adicionar:
- ``||basic:mostrar número 0||``
- ``||basic:pause 120||``
- ``||basic:limpar tela||``
- **``lendo = verdadeiro``**.

```blocks
let lendo = false
let b0 = 0
let b1 = 0
basic.forever(function () {
    b0 = pins.digitalReadPin(DigitalPin.P0)
    b1 = pins.digitalReadPin(DigitalPin.P1)
    if (!(lendo)) {
        if (b0 == 1 && b1 == 0) {
            basic.showNumber(0)
            basic.pause(120)
            basic.clearScreen()
            lendo = true
        } else if (b1 == 1 && b0 == 0) {
        }
    } else if (b1 == 0 && b0 == 0) {

    }
})
```

---
## {Detectar o novo bit}
Dentro de ``||logic:senão||`` vamos adicionar os mesmos blocos do ``||logic:se||``, mas trocar:
- ``||basic:mostrar número 0||`` para - ``||basic:mostrar número 1||``

```blocks
let lendo = false
let b0 = 0
let b1 = 0
basic.forever(function () {
    b0 = pins.digitalReadPin(DigitalPin.P0)
    b1 = pins.digitalReadPin(DigitalPin.P1)
    if (!(lendo)) {
        if (b0 == 1 && b1 == 0) {
            basic.showNumber(0)
            basic.pause(120)
            basic.clearScreen()
            lendo = true
        } else if (b1 == 1 && b0 == 0) {
            basic.showNumber(1)
            basic.pause(120)
            basic.clearScreen()
            lendo = true
        }
    } else if (b1 == 0 && b0 == 0) {

    }
})
```

---

## {Esperar o pulso terminar}
Para aceitar o **próximo** bit, precisamos que **ambos** os pinos voltem a **0**.  
Ainda no para isso no último bloco ``||basic:senão||`` adicione:
- **``lendo = falso``**.

No final do `sempre`, adicione uma **``||basic:pausa 5||``**.

```blocks
let lendo = false
let b0 = 0
let b1 = 0
basic.forever(function () {
    b0 = pins.digitalReadPin(DigitalPin.P0)
    b1 = pins.digitalReadPin(DigitalPin.P1)

    if (!(lendo)) {
        if (b0 == 1 && b1 == 0) {
            basic.showNumber(0)
            basic.pause(120)
            basic.clearScreen()
            lendo = true
        } else if (b1 == 1 && b0 == 0) {
            basic.showNumber(1)
            basic.pause(120)
            basic.clearScreen()
            lendo = true
        }
    } else if (b0 == 0 && b1 == 0) {
            lendo = false
    }

    basic.pause(5)
})
```

---

## {Teste}
1. Carregue este programa no **RECEPTOR**.  
2. Carregue o **EMISSOR** (que envia 0 no P0 e 1 no P1).  
3. Aperte **A** no emissor para enviar a sequência.  
4. O receptor deve **piscar 0 e 1** a cada **novo** bit (mesmo quando forem iguais seguidos).

> Se algum bit não aparecer, aumente um pouco o tempo do bit no emissor (ex.: **300 ms**) ou a pausa do receptor (ex.: **10–15 ms**).

```template
basic.forever(function () { })
```