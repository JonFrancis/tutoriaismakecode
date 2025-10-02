# Termômetro sem fio – **RECEPTOR**

## {Configurar o rádio}
Na categoria ``||radio:rádio||``, arraste **``||radio:definir grupo para||``** e troque para **o número dado pelo professor ao seu grupo** (o mesmo do emissor).

```blocks
radio.setGroup(999)
```

## {Guardar a temperatura recebida}
Em ``||radio:rádio||``, adicione **``||radio:ao receber rádio||``**.  
Crie a variável ``||variables:temp||`` (``||variables:Variáveis||``). Dentro do evento:
1. Use ``||logic:se … então||`` com condição **``name = "T"``**.  
2. *Então*: **``||variables:definir temp para valor||``**.

```blocks
let temp = 0
radio.onReceivedValue(function (name, value) {
    if (name == "T") {
        temp = value
    }
})
```

## {Mostrar a temperatura}
Em ``||basic:Básico||``, adicione **``||basic:sempre||``**. Dentro dele:  
- **``||basic:mostrar número||``** com ``||variables:temp||``;  
- **``||basic:pausa (ms)||``** com **300**.

```blocks
let temp = 0
basic.forever(function () {
    basic.showNumber(temp)
    basic.pause(300)
})
```

## {Teste}
Baixe no **Receptor**. Ao ligar o emissor, os números devem aparecer no display do micro:bit.
