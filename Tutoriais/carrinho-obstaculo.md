```package
github:microsoft/microbit-robot
```
# Carrinho que desvia de obstáculos

## {Iniciar o robô e o rádio}
Use o **grupo de rádio** indicado pelo(a) professor(a).

```blocks
radio.setGroup(1)
robot.yahboomTinyBit.start()
```

## {Variável}
Crie as ``||variables:Variáveis||``:

1. ``||variables:cmd||`` é o nosso comando, vamos iniciar ele em 4, pois é o comando para o carrinho ficar parado.
2. ``||variables:ultimo||`` serve para salvarmos o momento em que o comando chegou, vamos iniciar em 0.
3. ``||variables:tempo||`` serve para testarmos se o carrinho parou de receber comandos, vamos iniciar em 400ms.

```blocks
let cmd = 4
let ultimo = 0
let tempo = 400
```

## {Guardar o comando}
Vamos utiliza o bloco ``||radio:ao receber rádio n||``.

E dentro desse bloco igualar nosso ``||variable:cmd||`` ao n enviado pelo rádio;

e igualar ultimo ao bloco ``||control:millis||``.

```blocks
let cmd = 4
let ultimo = 0
radio.onReceivedNumber(function (n) {
    cmd = n
    ultimo = control.millis()
})
```

## {Parar}
Dentro do bloco ``||basic:sempre||`` vamos adicionar um bloco de ``||logic:se ... senão||``.

E como condição do ``||logic:se||``,``||control:millis||`` - ``||variable:ultimo||`` > tempo. 

Isso vai testar se nosso último comando foi enviado faz algum tempo.

```blocks
let tempo = 400
let ultimo = 0
basic.forever(function () {
    if (control.millis() - ultimo > tempo) {
    } else {
    }
})
```

## {Parar}
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

## {Andar para frente}
Dentro de ``||logic:senão||`` vamos criar uma lista de condições.
1. Comece pegando um bloco ``||logic:se ... senão||``.
2. A condição no ``||logic:se||`` é ``||variable::cmd||`` = 0;
3. Dentro do ``||logic:se||`` devemos fazer o carrinho andar para frente com ``||robot:motor tank 100% 100%||``.

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

## {Andar para direita}
1. Aperte no **+** abaixo do ``||logic:senão||``.
2. A condição do novo ``||logic:se||`` é ``||variable::cmd||`` = 1;
3. Dentro do ``||logic:se||`` devemos fazer o carrinho andar para direita com ``||robot:motor tank 0% 100%||``.

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

## {Andar para esquerda}
1. Aperte no **+** abaixo do ``||logic:senão||``.
2. A condição no novo ``||logic:se||`` é ``||variable::cmd||`` = 2;
3. Dentro do ``||logic:se||``  devemos fazer o carrinho andar para esquerda com ``||robot:motor tank 100% 0%||``.

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

## {Andar para trás}
1. Aperte no **+** abaixo do ``||logic:senão||``.
2. A condição no novo ``||logic:se||`` é ``||variable::cmd||`` = 3;
3. Dentro do ``||logic:se||`` devemos fazer o carrinho andar para trás com ``||robot:motor tank -100% -100%||``.

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

## {Parar}
Se não foram enviado comandos, vamos adicionar no ``||logic:senão||``:

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

## {Pausa}
Adicione uma ``||basic:pausa 20||`` ao final do código.

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

## {Desvia de obstáculos}
Para que o robô desvie de obstáculos vamos criar a ``||variable:Variável||`` distância.

Dentro do primeiro se (quando o carrinho anda pra frente), vamos ``||variable:definir distância para||`` ``||robot:robot obstacle distance (cm)||``.

```blocks
let cmd = 4
basic.forever(function () {
    if (cmd == 0) {
        let distância = robot.obstacleDistance()
        robot.motorTank(100, 100)
    } 
})
```

## {Desvia de obstáculos}
Agora vamos criar um ``||logic:se||`` para verificar se estamos próximos à um obstáculo. A condição deve ser ``||logic:se distância <=15||``. E dentro dele vamos fazer:
1. ``||robot:robot motor stop||`` => para o robô
2. ``||basic:pausa 100||`` => fica parado por 100ms
3. ``||robot:robot motor tank -100% -100%||`` => anda para trás
4. ``||basic:pausa 200||`` => anda por 200 ms
5. ``||robot:robot motor stop||`` => para o robô
6. ``||basic:pausa 100||`` => fica parado por 100ms
7. ``||robot:robot motor tank 100% 0%||`` => anda para o lado
8. ``||basic:pausa 200||`` => anda para o lado por 200 ms
9. ``||robot:robot motor stop||`` => para o robô

```blocks
let cmd = 4
basic.forever(function () {
    if (cmd == 0) {
        let distância = robot.obstacleDistance()
        if (distância <= 15){
            robot.motorStop()
            basic.pause(100)
            robot.motorTank(-100, -100)
            basic.pause(200)
            robot.motorStop()
            basic.pause(100)
            robot.motorTank(100, 0)
            basic.pause(200)
            robot.motorStop()
        }
    } 
})
```

## {Teste}
- Conecte o @boardname@ e baixe o programa nele.  
- Conecte o @boardname@ no carrinho tiny:bit.
- Ligue o carrinho e o micro:bit controle remoto e teste os comandos.

```template
radio.setGroup(1)
robot.yahboomTinyBit.start()
```