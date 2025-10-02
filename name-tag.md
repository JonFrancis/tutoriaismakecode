---
title: Name Tag - Crachá
description: Transforme seu micro:bit em um crachá digital
author: João Francisco - Br.ino
---

# Name Tag - Crachá

## Transforme seu micro:bit em um crachá digital @unplugged

Veja seu nome em 💡 luzes! 💡 Programe o micro:bit para rolar seu nome pela tela.

![Nome rolando nos LEDs](https://raw.githubusercontent.com/BrinoOficial/name-tag/ad304e87becb5a3e14f885e1f7d31a0fd40a8601/name-tag-menor.gif)

## {Step 1}

Clique na categoria ``||basic:Básico||`` na Caixa de Ferramentas. 
Arraste um bloco ``||basic:mostrar string||`` para dentro do bloco ``||basic:sempre||``. 
Depois, no bloco ``||basic:mostrar string||``, troque o texto de "Hello!" para o seu nome.

```blocks
basic.forever(function() {
    basic.showString("Br.ino");
})
```

## {Step 2}

Olhe o simulador @boardname@ na tela. Você vê seu nome rolando? ⭐ Ótimo trabalho! ⭐ Você transformou o micro:bit em um crachá digital!

## {Step 3}

Se você tiver um dispositivo @boardname@, conecte-o ao computador e clique no botão ``|Download|``. Siga as instruções para transferir seu código para o @boardname@ e veja seu nome aparecer em luzes!

## {Step 4}

Vá além — tente adicionar mais blocos ``||basic:mostrar string||`` para criar uma história!.

```template
basic.forever(function() {})
```