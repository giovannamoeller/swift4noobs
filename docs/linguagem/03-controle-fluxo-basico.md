# Controle de fluxo básico

## Condicionais
As condicionais permitem que o programa faça algo somente se uma determinada condição é verdadeira.
A condição, portanto, retorna um valor booleano: true/false. É nesse momento que entram os operadores relacionais/lógicos.

### If / else
Se uma condição for verdadeira, executará uma instrução. Se não, executará outra instrução. Veja um exemplo abaixo:
```swift
let idade = 21

if idade >= 18 {
    print("Você pode dirigir!")
} else {
    print("Você não pode dirigir!")
}
```

### If / else if / else

O `else if` cria uma outra condição a ser testada. Veja um exemplo abaixo:

```swift
let numero1 = 20
let numero2 = 30

if numero1 > numero2 {
    print("Número 1 é maior que número 2")
} else if numero1 < numero2 {
    print("Número 2 é maior que número 1")
} else {
    print("Número 1 e número 2 são iguais")
}
```

### Operador ternário

O operador ternário é um modo mais curto e mais simples de executar um `if-else`. Veja um exemplo abaixo:
```swift
let idade = 20

idade >= 18 ? print("Pode dirigir") : print("Não pode dirigir")
```

## Loops
Loops são um modo de executar código múltiplas vezes, ou seja, repetindo um bloco de código até uma condição de parada. 

### While
O comando while repete uma instrução enquanto ela for verdadeira. 
O loop verifica a condição para cada iteração. Se a condição for verdadeira, então o loop é executado e passa para outra iteração. Se a condição for falsa, então o loop para. 

Veja o exemplo abaixo:
```swift
var count = 1
while count < 10 {
    count += 1
}
print(count) // 10
```

### Repeat While
É extremamente parecido com o `while`, porém no `repeat-while` você executa uma instrução pela primeira vez sem checar a sua condição, já que a condição é checada apenas no final. Isso não acontece com o `while`, que desde a primeira instrução já checa a condição.

Em outras linguagens, você pode conhecer esse comando como `do-while`.

```swift
var count = 1
repeat {
    count += 1
} while (count < 10)
print(count) // 10
```

### Saindo de um loop
Caso você queira sair de um loop antes da condição, você pode utilizar uma palavra `break`, que para imediatamente a execução do loop.

```swift
var count = 1
while true {
    if count > 10 {
        break
    }
    count += 1
}
print(count) // 11
```

### Forçando a próxima iteração do loop
Podemos pular uma iteração com o comando `continue`, forçando a próxima iteração daquele loop. Veja o exemplo abaixo:

```swift
var count = 0
while count < 10 {
    count += 1
    if count == 5 {
        continue
    }
    print(count) // quando count for 5, ele não será printado, porque força a próxima iteração do loop
}
```