# Controle por Inclinação

## Mova o carrinho inclinando o controle @boardname@

Vamos usar a inclinação do @boardname@ para enviar comandos pelo rádio:

- **Logo para cima** → **0 (frente)**
- **Inclinar para a direita** → **1 (direita)**
- **Inclinar para a esquerda** → **2 (esquerda)**
- **Logo para baixo** → **3 (trás)**
- **Neutro** (sem inclinar) → **4 (parar)**

## {Configurar o rádio}
Use o **grupo de rádio** indicado pelo(a) professor(a).

```blocks
radio.setGroup(1)
```

## {Criar a variável do comando}
Crie a variável ``||variables:cmd||`` e inicie em **4**.

```blocks
let cmd = 4
```

## {Salvando o comando pela inclinação}
Dentro de ``||basic:sempre||`` vamos:
1. Começar com **neutro** (`cmd = 4`).
2. Criar uma sequência de ``||logic:se... senão se||``.
3. ``||logic:se||``, a condição deve ser ``||input:is logotipo para cima gesture||`` => cmd = 0,
4. ``||logic:senão se||`` ``||input:is inclinar para a direita gesture||`` => cmd = 1,
5. ``||logic:senão se||`` ``||input:is inclinar para a esquerda gesture||`` => cmd = 2,
6. ``||logic:senão se||`` ``||input:is logotipo para baixo gesture||`` => cmd = 3,


```blocks
let cmd = 4
basic.forever(function () {
    cmd = 4
    if (input.isGesture(Gesture.LogoUp)) {
        cmd = 0  // frente
    } else if (input.isGesture(Gesture.TiltRight)) {
        cmd = 1  // direita
    } else if (input.isGesture(Gesture.TiltLeft)) {
        cmd = 2  // esquerda
    } else if (input.isGesture(Gesture.LogoDown)) {
        cmd = 3  // trás
    }
})
```

## {Enviar o comando}
Após a última condição ``||logic:se senão||`` envie o cmd pelo rádio com:
1. ``||radio:rádio envia número cmd||``
2. ``||basic:pausa 100||``


```blocks
let cmd = 4
basic.forever(function () {
    cmd = 4
    if (input.isGesture(Gesture.LogoUp)) {
        cmd = 0  // frente
    } else if (input.isGesture(Gesture.TiltRight)) {
        cmd = 1  // direita
    } else if (input.isGesture(Gesture.TiltLeft)) {
        cmd = 2  // esquerda
    } else if (input.isGesture(Gesture.LogoDown)) {
        cmd = 3  // trás
    }
    radio.sendNumber(cmd)
    basic.pause(150)
})
```

## {Teste}
- Conecte seu @boardname que será o controle remoto e aperte no botão ``||Baixar||``.    

```template
radio.setGroup(1)
let cmd = 4
```
