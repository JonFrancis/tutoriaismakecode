# Controle remoto

## Envie números pelo rádio para dirigir o robô @unplugged

Vamos usar o @boardname@ para enviar sinais de rádio. O robô recebe e transforma em movimento.

- **A+B → 0 (frente)**  
- **B → 1 (direita)**  
- **A → 2 (esquerda)**  
- **Símbolo do @boardname@ → 3 (trás)**  
- **Nenhum** → 4 (neutro)

## {Configurar o rádio}
Use o **grupo de rádio** indicado pelo(a) professor(a).

```blocks
radio.setGroup(1)
```

## {Variável}
Crie a variável ``||variable:cmd||`` que enviará nosso comando, e inicie em 4. 

```blocks
basic.forever(function () {
    let cmd = 4
}
```

## {Enviar o comando}
Dentro de ``||basic:sempre||``: 
1. Começar com **neutro** (`cmd = 4`).
2. Criar uma sequência de ``||logic:se... senão se||``.
3. ``||logic:se||``, a condição deve ser ``||input:botão A+B é pressionado||`` => cmd = 0,
4. ``||logic:senão se||`` ``||input:botão B é pressionado||`` => cmd = 1,
5. ``||logic:senão se||`` ``||input:botão A é pressionado||`` => cmd = 2,
6. ``||logic:senão se||`` ``||input:logotipo é pressionado||`` => cmd = 3, 

```blocks
basic.forever(function () {
    let cmd = 4
    if (input.buttonIsPressed(Button.AB)) {
        cmd = 0
    } else if (input.buttonIsPressed(Button.B)) {
        cmd = 1
    } else if (input.buttonIsPressed(Button.A)) {
        cmd = 2
    } else if (input.logoIsPressed()) {
        cmd = 3
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
    let cmd = 4
    if (input.buttonIsPressed(Button.AB)) {
        cmd = 0
    } else if (input.buttonIsPressed(Button.B)) {
        cmd = 1
    } else if (input.buttonIsPressed(Button.A)) {
        cmd = 2
    } else if (input.logoIsPressed()) {
        cmd = 3
    }
    radio.sendNumber(cmd)
    basic.pause(150)
})
```

## {Teste}
- Conecte seu @boardname que será o controle remoto e aperte no botão ``||Baixar||``.  

```template
basic.forever(function () { })
```
