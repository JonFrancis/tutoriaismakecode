# Contador de Passos

## {Variável}
 
Na categoria ``||variables:Variáveis||``. Crie uma variável chamada **passos**.

E dentro do bloco ``||basic:no iniciar||`` use ``||variables:definir passos||`` e mude o número para 0.

```blocks
let passos = 0
```

## {Registrar Passos}

Vamos registrar um passo sempre que o micro:bit for chacoalhado. 

Arraste o bloco ``||input:ao sacudir||``.

```blocks
input.onGesture(Gesture.Shake, function () {})
```

## {Registrar Passos}

Arraste um bloco ``||variables:alterar passos||`` para dentro do bloco ``||input:em agitar||``.

```blocks
let passos = 0
input.onGesture(Gesture.Shake, function () {
    passos += 1
})
```

## {Mostre os passos}

Arraste um bloco ``||basic:mostrar número||`` para dentro do bloco ``||input:em agitar||``, logo abaixo do bloco ``||variables:mudar passos||``.

```blocks
let passos = 0
input.onGesture(Gesture.Shake, function () {
    passos += 1
    basic.showNumber(0)
})
```

## {Mostre os passos}

Arraste sua variável ``||variables:passos||`` substituindo o 0 em ``||basic:mostrar número||``.

```blocks
let passos = 0
input.onGesture(Gesture.Shake, function () {
    passos += 1
    basic.showNumber(passos)
})
```

## {Conecte ao micro:bit}

Conecte o @boardname@ ao computador e clique no botão ``|Baixar|``.

Teste seu contador de passos.