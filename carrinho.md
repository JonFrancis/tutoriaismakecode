```package
github:microsoft/microbit-robot
```
# Tiny:bit — **RECEPTOR**

## Receba números e mova o robô @unplugged

---

## {Iniciar o robô e o rádio}
Use o mesmo **grupo** do transmissor.

```blocks
radio.setGroup(1)
robot.yahboomTinyBit.start()
```

---

## {Variável}
Crie as ``||variables:Variáveis||`` **cmd**, **ultimo** e **tempo**.

-``||variables:cmd||`` é o nosso comando, vamos iniciar ele em 4, pois é o comando para o carrinho ficar parado.

-``||variables:ultimo||`` serve para salvarmos o momento em que o comando chegou, vamos iniciar em 0.

-``||variables:tempo||`` serve para testarmos se o carrinho parou de receber comandos, vamos iniciar em 400 (que será equivalente a 0,4 segundos).

```blocks
let cmd = 4
let ultimo = 0
let tempo = 400
```

---

## {Guardar o comando}
Vamos utiliza o bloco ``||radio:ao receber rádio n||``.

E dentro desse bloco fazer ``||variable:cmd||`` = n;

e ultimo = ``||control:millis||``.


```blocks
let cmd = 4
let ultimo = 0
radio.onReceivedNumber(function (n) {
    cmd = n
    ultimo = control.millis()
})
```

---

## {Fazer o carrinho andar com os comandos}
Dentro do bloco ``||basic:sempre||`` vamos adicionar um bloco de ``||logic:se ... senão||``.

A condição do ``||logic:se||`` vai ser:

- ``||control:millis||`` - ``||variable:ultimo||`` > tempo. Isso vai testar se nosso último comando foi enviado faz algum tempo.

```blocks
let tempo = 400
let ultimo = 0
basic.forever(function () {
    if (control.millis() - ultimo > tempo) {
    } else {
    }
})
```

---
## {Fazer o carrinho andar com os comandos}
Dentro do bloco ``||logic:se||`` devemos parar o carrinho adicionando o comando:

- ``||robot:robot motor stop||``.

```blocks
let tempo = 400
let ultimo = 0
basic.forever(function () {
    if (control.millis() - ultimo > tempo) {
        robot.motorStop()
    } else {
    }
})
```

---

## {Fazer o carrinho andar com os comandos}
Dentro de ``||logic:senão||`` vamos criar uma lista de condições.

Comece pegando um bloco ``||logic:se ... senão||``.

Para o carrinho andar pra frente, vamos adicionar:

- A condição no ``||logic:se||`` é ``||variable::cmd||`` = 0;

- Dentro do se deve ter ``||robot:motor tank 100% 100%||``.
```blocks
let tempo = 400
let ultimo = 0
let cmd = 4
basic.forever(function () {
    if (control.millis() - ultimo > tempo) {
        robot.motorStop()
    } else {
        if (cmd == 0) {
            robot.motorTank(100, 100)
        } else {  
        }
    }

})
```

---

## {Fazer o carrinho andar com os comandos}
Aperte no **+** abaixo do ``||logic:senão||``.

Para o carrinho andar pra direita, vamos adicionar:

- A condição no ``||logic:se||`` é ``||variable::cmd||`` = 1;

- Dentro do se deve ter ``||robot:motor tank 0% 100%||``.

```blocks
let tempo = 400
let ultimo = 0
let cmd = 4
basic.forever(function () {
    if (control.millis() - ultimo > tempo) {
        robot.motorStop()
    } else {
        if (cmd == 0) {
            robot.motorTank(100, 100)
        } else if (cmd == 1){
            robot.motorTank(0, 100)
        } else {
        }
    }

})
```

---

## {Fazer o carrinho andar com os comandos}
Aperte no **+** abaixo do ``||logic:senão||``.

Para o carrinho andar pra esquerda, vamos adicionar:

- A condição no ``||logic:se||`` é ``||variable::cmd||`` = 2;

- Dentro do se deve ter ``||robot:motor tank 100% 0%||``.

```blocks
let tempo = 400
let ultimo = 0
let cmd = 4
basic.forever(function () {
    if (control.millis() - ultimo > tempo) {
        robot.motorStop()
    } else {
        if (cmd == 0) {
            robot.motorTank(100, 100)
        } else if (cmd == 1){
            robot.motorTank(0, 100)
        } else if (cmd == 2){
            robot.motorTank(100, 0)
        } else {
        }
    }

})
```

---

## {Fazer o carrinho andar com os comandos}
Aperte no **+** abaixo do ``||logic:senão||``.

Para o carrinho andar pra trás, vamos adicionar:

- A condição no ``||logic:se||`` é ``||variable::cmd||`` = 3;

- Dentro do se deve ter ``||robot:motor tank -100% -100%||``.

```blocks
let tempo = 400
let ultimo = 0
let cmd = 4
basic.forever(function () {
    if (control.millis() - ultimo > tempo) {
        robot.motorStop()
    } else {
        if (cmd == 0) {
            robot.motorTank(100, 100)
        } else if (cmd == 1){
            robot.motorTank(0, 100)
        } else if (cmd == 2){
            robot.motorTank(100, 0)
        } else if (cmd == 3){
            robot.motorTank(-100, -100)
        } else {
        }
    }

})
```

---

## {Fazer o carrinho andar com os comandos}
Para o carrinho andar pra trás, vamos adicionar no ``||logic:senão||``:

- ``||robot:robot motor stop||``.

```blocks
let tempo = 400
let ultimo = 0
let cmd = 4
basic.forever(function () {
    if (control.millis() - ultimo > tempo) {
        robot.motorStop()
    } else {
        if (cmd == 0) {
            robot.motorTank(100, 100)
        } else if (cmd == 1){
            robot.motorTank(0, 100)
        } else if (cmd == 2){
            robot.motorTank(100, 0)
        } else if (cmd == 3){
            robot.motorTank(-100, -100)
        } else {
            robot.motorStop()
        }
    }
})
```

---

## {Finalizar}
Para finalizar adicione uma pause de 20 ms ao final do código.

```blocks
let tempo = 400
let ultimo = 0
let cmd = 4
basic.forever(function () {
    if (control.millis() - ultimo > tempo) {
        robot.motorStop()
    } else {
        if (cmd == 0) {
            robot.motorTank(100, 100)
        } else if (cmd == 1){
            robot.motorTank(0, 100)
        } else if (cmd == 2){
            robot.motorTank(100, 0)
        } else if (cmd == 3){
            robot.motorTank(-100, -100)
        } else {
            robot.motorStop()
        }
    }
    basic.pause(20)
})
```

---

## {Teste}
- Conecte o @boardname@ e baixe o programa nele.  
- Conecte o @boardname@ no carrinho tiny:bit.
- Ligue o carrinho e o micro:bit controle remoto e teste os comandos.

```template
// Carregado automaticamente quando o tutorial abrir
radio.setGroup(1)
robot.yahboomTinyBit.start()
```