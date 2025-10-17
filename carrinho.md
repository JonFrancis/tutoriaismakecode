# Tiny:bit — **RECEPTOR**

```package
github:microsoft/microbit-robot
```

## Receba números e mova o robô @unplugged

`||robot:robot ... start||` O robô vai escutar o rádio e aplicar o comando. Se ficar um tempinho **sem receber**, ele **para** (segurança).

- **0 = frente**  
- **1 = direita**  
- **2 = esquerda**  
- **3 = trás**  
- **outros (4/neutro)** = parar

---

## {Iniciar o robô e o rádio}
Use o mesmo **grupo** do transmissor.

```blocks
radio.setGroup(1)
// @highlight
robot.yahboomTinyBit.start()
```

---

## {Ler os números recebidos}
Guarde o último comando e **o momento** em que chegou (para o temporizador).

```blocks
let cmd = 4
let ultimoRx = 0
radio.onReceivedNumber(function (n) {
    cmd = n
    ultimoRx = control.millis()
})
```

---

## {Aplicar o comando + segurança (timeout)}
Se **passar muito tempo** sem receber nada, **pare** os motores.

```blocks
let TIMEOUT = 400
basic.forever(function () {
    if (control.millis() - ultimoRx > TIMEOUT) {
        robot.motorStop()
    } else {
        if (cmd == 0) {
            robot.motorTank(100, 100)      // frente
        } else if (cmd == 1) {
            robot.motorTank(100, 0)        // direita
        } else if (cmd == 2) {
            robot.motorTank(0, 100)        // esquerda
        } else if (cmd == 3) {
            robot.motorTank(-100, -100)    // trás
        } else {
            robot.motorStop()              // neutro
        }
    }
    basic.pause(20)
})
```

> Dica: para movimentos mais suaves, troque `100` por `60`.

---

## {Teste}
- Baixe no **Tiny:bit**.  
- Com o transmissor ligado, segure **A+B** (frente), **B** (direita), **A** (esquerda) ou **sacuda** (trás).  
- Ao soltar/parar de sacudir, ele volta a **neutro**; se o transmissor apagar, o **timeout** para o robô.

```template
// Carregado automaticamente quando o tutorial abrir
radio.setGroup(1)
robot.yahboomTinyBit.start()
```