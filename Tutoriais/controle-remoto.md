# Controle do Tiny:bit — **TRANSMISSOR (micro:bit)**

## Envie números pelo rádio para dirigir o robô @unplugged

Vamos usar o @boardname@ para enviar sinais de rádio. O robô (tiny:bit) recebe e transforma em movimento.

- **A+B → 0 (frente)**  
- **B → 1 (direita)**  
- **A → 2 (esquerda)**  
- **Símbolo do @boardname@ → 3 (trás)**  
- **Nenhum** → 4 (neutro)

---

## {Configurar o rádio}
Na aba ``||radio:rádio||``, coloque o grupo que o professor solicitou.

```blocks
radio.setGroup(1)
```

---

## {Variável}
Crie a variável `cmd` que mandará nosso comando, e inicie ela em 4. 

```blocks
basic.forever(function () {
    let cmd = 4
}
```

---

## {Enviar o comando atual}
No ``||basic:sempre||``:  
1. Leia entradas na ordem abaixo e troque o comando enviado:
   - ``||logic:se||`` **A+B** → `cmd = 0`
   - ``||logic:senão se||`` **B** → `cmd = 1`
   - ``||logic:senão se||`` **A** → `cmd = 2`
   - ``||logic:senão se||`` ||input:logotipo é pressionado||`` → `cmd = 3`
3. **Envie o número** pelo rádio com o bloco ``||radio:rádio envia número||``.  
4. E por fim adicione o bloco ``||basic:pause(ms) 150||``.

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
    radio.sendNumber(cmd)
    basic.pause(150)
})
```

---

## {Teste}
- Conecte seu @boardname@ no computador e baixe o programa clicando em Baixar.
- Faça o próximo tutorial no site indicado no livro.

```template
basic.forever(function () { })
```
