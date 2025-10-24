# Termômetro sem fio – **RECEPTOR**

## {Configurar o rádio}
Use o **grupo de rádio** indicado pelo(a) professor(a).

```blocks
radio.setGroup(1)
```
## {Variável}
Crie a variável ``||variables:temp||`` e use ``||variables:definir temp para 0||`` no bloco ``||basic:no iniciar||``. 

```blocks
basic.forever(function () {
    let temp = input.temperature()
})
```

## {Guardar a temperatura recebida}
Adicione o bloco ``||radio:ao receber rádio||``.  
E dentro dele:
1. Use ``||logic:se … então||`` com condição ``||logic:=||``.
2. No primeiro espaço de ``||logic:=||`` arraste o name do bloco de cima.
3. No segundo espaço escreva T
3. No ``||logic:senão||`` adicione o bloco ``||variables:definir temp para||`` e arraste valor do bloco de cima para cá.

```blocks
let temp = 0
radio.onReceivedValue(function (name, value) {
    if (name == "T") {
        temp = value
    }
})
```

## {Mostrar a temperatura}
Dentro de ``||basic:sempre||``:  
- ``||basic:mostrar número||`` ``||variables:temp||``;  
- ``||basic:pausa 300(ms)||``.

```blocks
let temp = 0
basic.forever(function () {
    basic.showNumber(temp)
    basic.pause(300)
})
```

## {Teste}
Baixe no **Receptor**. Ao ligar o emissor, os números devem aparecer no display do micro:bit.
