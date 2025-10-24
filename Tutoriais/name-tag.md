# Name Tag - Crachá

## Transforme seu micro:bit em um crachá digital @unplugged

Veja seu nome em 💡 luzes! 💡 Programe o micro:bit para rolar seu nome pela tela.

![Nome rolando nos LEDs](https://raw.githubusercontent.com/BrinoOficial/TutoriaisMakeCode/master/name-tag-menor.gif)

## {Código}

Arraste um bloco ``||basic:mostrar string||`` para dentro do bloco ``||basic:sempre||``. 

Depois, no bloco ``||basic:mostrar string||``, troque o texto de "Hello!" para o seu nome.

```blocks
basic.forever(function() {
    basic.showString("Br.ino");
})
```

## {Colocando o Còdigo no micro:bit}

Conecte o @boardname@ no computador e clique no botão ``|Download|``.

⭐ Ótimo trabalho! ⭐ Você transformou o micro:bit em um crachá digital!

```template
basic.forever(function() {})
```