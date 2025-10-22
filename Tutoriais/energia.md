# Energizando uma entrada

## Aprendendo a ligar e controlar um LED com o @boardname@ @unplugged
![Imagem da Montagem](https://raw.githubusercontent.com/BrinoOficial/TutoriaisMakeCode/master/LEDMicrobit.png)

> Talvez nada aconteça **sem código** — é normal! Diferente do **3V**, as portas **P0/P1/P2** só "ligam" quando **programamos**.

## {Vamos ligar o P0}
Vamos "energizar" a porta **P0** por código.

Na aba ``||advanced:Avançado||`` na categoria ``||pins:Pins||``, arraste **``||pins:escrever pino P0 para 1||``** para dentro de ``||basic:no iniciar||``.

```blocks
pins.digitalWritePin(DigitalPin.P0, 1)
```

> Agora ao apertar em ``||Baixar||`` o LED deve acender.

---

## {Piscar o LED}
Agora vamos fazer o LED **piscar**.

Em ``||basic:Básico||``, use **``||basic:sempre||``** e dentro dele:
1. **``||pins:escrever pino P0 para 1||``**
2. **``||basic:pausa (ms)||``** com **500**
3. **``||pins:escrever pino P0 para 0||``**
4. **``||basic:pausa (ms)||``** com **500**

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P0, 0)
    basic.pause(500)
})
```

> Ajuste a **pausa** para piscar mais rápido/devagar (100 = rápido, 1000 = lento).

---

## {Botão liga/desliga}
Vamos controlar o LED com o **botão A**.  
Crie a variável ``||variables:ligado||``. 
Em ``||input:Entrada||`` arraste ``||input:no botão A pressionado||``

```blocks
let ligado = false
input.onButtonPressed(Button.A, function () {
ligado = !(ligado)
})
```

---

## {Botão liga/desliga}
Agora vamos adicionar o bloco ``||logic:se, então... senão||`` 
Vamos adicionar ``||variables:ligado||`` após o ``||logic:se||``

```blocks
let ligado = false
input.onButtonPressed(Button.A, function () {
    ligado = !(ligado)
    if (ligado) {   
    } else {
    }
})
```

---
## {Botão liga/desliga}
Em ``||logic:se ligado então||`` vamos adicionar ``||pins:gravação digital||`` selecionar o pin P0 e após "para" vamos colocar o número 1.
Em "else" vamos fazer a mesma coisa, mas mudar o número para 0

```blocks
let ligado = false
input.onButtonPressed(Button.A, function () {
    ligado = !(ligado)
    if (ligado) {   
        pins.digitalWritePin(DigitalPin.P0, 1)
    } else {
        pins.digitalWritePin(DigitalPin.P0, 0)
    }
})
```
---

---
## {Botão liga/desliga}
> Agora ao apertar em ``||Baixar||`` o botão A deve funcionar como uma chave para o LED. 

---

## {Desafio}
1. **Economia inteligente:** faça o LED apagar sozinho após **10 s** ligado.  

---