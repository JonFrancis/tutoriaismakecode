# Termômetro sem fio – **EMISSOR**

## {Configurar o rádio}
Use o **grupo de rádio** indicado pelo(a) professor(a).

```blocks
radio.setGroup(1)
```
## {Variável}
Crie a variável ``||variables:temp||`` e use ``||variables:definir temp para||`` ``||input:temperatura (°C)||``. 

```blocks
basic.forever(function () {
    let temp = input.temperature()
})
```

## {Enviar a temperatura}
Abaixo da definição da variável adicione : 
1. ``||radio:rádio envia value T = temp||``.
2. ``||basic:pausa 1000(ms)||``.

```blocks
basic.forever(function () {
    let temp = input.temperature()
    radio.sendValue("T", temp)
    basic.pause(1000)
})
```

## {Teste}
Baixe no **Emissor** e confirme que está tudo certo.

Ele envia a temperatura a cada 1 segundo.
