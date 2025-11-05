```package
github:microsoft/microbit-robot
```
# Carrinho seguidor de linha
## {Base}
A base do código já inicia nosso carrinho e inicia os comandos de seguidor de linha.
```blocks
robot.yahboomTinyBit.start()
robot.setAssist(RobotAssist.LineFollowing, true)
```
## {Carrinho fora da linha}
Se o carrinho está fora da linha vamos colocar ele para ficar girando até encontrar um linha com:
1. ``||robot:robot on line off off||``
2. Dentro do bloco anterior adicionar ``||robot:robot motor tank 100 0||`` 
```blocks
robot.onLineLeftRightDetected(false, false, function () {
    robot.motorTank(100, 0)
})
```
## {Carrinho na linha}
Se o carrinho na linha vamos fazer com que ele ande para frente:
1. ``||robot:robot on line on on||``
2. Dentro do bloco anterior adicionar ``||robot:robot motor tank 100 100||`` 
```blocks
robot.onLineLeftRightDetected(true, true, function () {
    robot.motorTank(100, 100)
})
```
## {Carrinho com a linha à direita}
Se o carrinho está detectando a linha à direita, ele deve andar pra direita para centralizar na linha:
1. ``||robot:robot on line off on||``
2. Dentro do bloco anterior adicionar ``||robot:robot motor tank 0 100||`` 
```blocks
robot.onLineLeftRightDetected(false, true, function () {
    robot.motorTank(0, 100)
})
```
## {Carrinho com a linha à esquerda}
Se o carrinho está detectando a linha à esquerda, ele deve andar pra esquerda para centralizar na linha:
1. ``||robot:robot on line on off||``
2. Dentro do bloco anterior adicionar ``||robot:robot motor tank 100 0||`` 
```blocks
robot.onLineLeftRightDetected(true, false, function () {
    robot.motorTank(100, 0)
})
```
```template
robot.yahboomTinyBit.start()
robot.setAssist(RobotAssist.LineFollowing, true)
```
