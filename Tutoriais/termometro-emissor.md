# Termômetro sem fio – **EMISSOR (simples)**

## {Configurar o rádio}
Na categoria ``||radio:rádio||``, arraste **``||radio:definir grupo do rádio||``** e troque para **o número indicado pelo professor** (o mesmo do receptor).

```blocks
radio.setGroup(999)
```

## {Enviar a temperatura}
Em ``||basic:Básico||``, adicione **``||basic:sempre||``**. Dentro dele:
1. Pegue ``||input:temperatura (°C)||`` (``||input:Entrada||``) e guarde em uma variável local ``temp``.  
2. Envie pelo rádio com **``||radio:rádio envia value||``**, escrevendo **T** no campo *name* e usando ``temp`` no *value*.  
3. Adicione **``||basic:pausa (ms)||``** com **1000**.

```blocks
basic.forever(function () {
    let temp = input.temperature()
    radio.sendValue("T", temp)
    basic.pause(1000)
})
```

## {Teste}
Baixe no **Emissor** e confirme que está tudo certo. Pronto! Ele envia a temperatura a cada 1 segundo.
