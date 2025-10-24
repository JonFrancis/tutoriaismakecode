```package
github:microsoft/audio-recording
```
# Gravador Secreto

## {Gravando}
Para gravar, vamos modificar o bloco ``||input:no botão A pressionado||``:
1. Arraste um bloco ``||basic:mostrar ícone||`` e escolha um desenho para representar quando está gravando.
2. Pegue um bloco ``||record:record audio clip until done||``, que vai gravar o áudio.
3. Limpe a tela com ``||basic:limpar tela||``

```blocks
input.onButtonPressed(Button.A, function () {
    record.setSampleRate(10000, record.AudioSampleRateScope.Recording)
    basic.showIcon(IconNames.SmallSquare)
    record.startRecording(record.BlockingState.Blocking)
    basic.clearScreen()
})
```

## {Reproduzindo}
Para reproduzir, vamos adicionar o bloco ``||input:no botão B pressionado||``, e dentro dele:
1. Pegue um bloco ``||record:set sample rate to 10000 for playback``||.
2. Arraste um bloco ``||basic:mostrar ícone||`` e escolha um desenho para representar quando está reproduzindo.
2. Pegue um bloco ``||record:play audio clip until done||``, que vai reproduzir o áudio.
3. Limpe a tela com ``||basic:limpar tela||``

```blocks
input.onButtonPressed(Button.B, function () {
    record.setSampleRate(10000, record.AudioSampleRateScope.Playback)
    basic.showLeds(`
        . # . . .
        . # # . .
        . # # # .
        . # # . .
        . # . . .
        `)
    record.playAudio(record.BlockingState.Blocking)
    basic.clearScreen()
})
```

## {Teste}
> Agora ao apertar em ``||Baixar||`` e teste seu gravador, o botão A irá gravar, e o botão B reproduzir.
> Como desafio tente modificar o número quando o B é pressionado, que está 10000, veja o que acontece quando você coloca números menores e maiores.


```template
input.onButtonPressed(Button.A, function () {
    record.setSampleRate(10000, record.AudioSampleRateScope.Recording)
})
```