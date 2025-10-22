# Contador de Passos

## Conte seus passos com o micro:bit! @unplugged

Transforme seu @boardname@ em um contador de passos. Vamos usar o sensor de movimento (acelerômetro) para identificar quando damos um passo com o micro:bit.

## {Passo 1}

Primeiro, precisamos criar uma variável para acompanhar o número de passos 🦶. Uma variável é um "recipiente" para guardar valores.  
Clique na categoria ``||variables:Variáveis||`` na Caixa de Ferramentas. Clique no botão **Fazer uma variável**. Dê o nome **"passos"** para a nova variável e clique em **OK**.

## {Passo 2}

Clique na categoria ``||variables:Variáveis||`` na Caixa de Ferramentas. Você notará que apareceram novos blocos. Arraste um bloco ``||variables:definir passos||`` para dentro do bloco ``||basic:no iniciar||``. Isso define o valor da variável ``||variables:passos||`` como **0** quando o programa inicia.

```blocks
let passos = 0
```

## {Passo 3}

Vamos registrar um passo sempre que o micro:bit for chacoalhado. Clique na categoria ``||input:Entrada||`` na Caixa de Ferramentas. Arraste um bloco ``||input:ao sacudir||`` para a área de trabalho e coloque-o em qualquer lugar.

```blocks
input.onGesture(Gesture.Shake, function () {})
```

## {Passo 4}

Clique na categoria ``||variables:Variáveis||`` na Caixa de Ferramentas. Arraste um bloco ``||variables:alterar passos||`` para dentro do bloco ``||input:em agitar||``. Agora, toda vez que sacudirmos o micro:bit (ou dermos um passo), vamos somar 1 ao valor da variável ``||variables:passos||``.

```blocks
let passos = 0
input.onGesture(Gesture.Shake, function () {
    passos += 1
})
```

## {Passo 5}

Vamos mostrar o número de passos dados. Clique na categoria ``||basic:Básico||`` na Caixa de Ferramentas. Arraste um bloco ``||basic:mostrar número||`` para dentro do bloco ``||input:em agitar||``, abaixo do bloco ``||variables:mudar passos||``.

```blocks
let passos = 0
input.onGesture(Gesture.Shake, function () {
    passos += 1
    basic.showNumber(0)
})
```

## {Passo 6}

Clique na categoria ``||variables:Variáveis||`` na Caixa de Ferramentas. Arraste um bloco ``||variables:passos||`` para dentro do bloco ``||basic:mostrar número||``, substituindo o número **0**.

```blocks
let passos = 0
input.onGesture(Gesture.Shake, function () {
    passos += 1
    basic.showNumber(passos)
})
```

## {Passo 7}

Conecte o @boardname@ ao computador e clique no botão ``|Baixar|``. Siga as instruções para transferir seu código para o @boardname@. Depois que o código for baixado, conecte o micro:bit a pilhas ou bateria. Ande por aí. O micro:bit está contando seus passos?