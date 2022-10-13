# Controle de fluxo básico

## Condicionais
As condicionais permitem que o programa faça algo somente se uma determinada condição é verdadeira.
A condição, portanto, retorna um valor booleano: true/false. É nesse momento que entram os operadores relacionais/lógicos.

### If / else
Se uma condição for verdadeira, executará uma instrução. Se não, executará outra instrução. 

Vamos pensar em uma situação na vida real: você só pode tirar carta de motorista se tiver mais de 18 anos aqui no Brasil, certo? Isso é uma condicional: **se** tiver mais de 18 anos, pode tirar carta. **Se não** for maior de 18 anos, não pode tirar carta.

Veja um exemplo abaixo representando a situação acima com código:

```swift
let idade = 21

if idade >= 18 {
    print("Você pode tirar carta!")
} else {
    print("Você não pode tirar carta!")
}
```

Agora pense que, para a pessoa dirigir, ela precisa ser maior de 18 anos **e** ter passado no exame do detran.

Podemos utilizar os operadores lógicos que vimos na página anterior para lidar com essa situação:

```swift
let idade = 21
let passouNoExameDoDetran = false

if idade >= 18 && passouNoExameDoDetran {
    print("Você pode dirigir!")
} else {
    print("Você não pode dirigir!!")
}
```

Perceba que `idade >= 18` retorna um valor booleano. Todas as condições dentro de um `if` retornam um valor booleano, true/1 ou false/0.

Quando falamos sobre valores booleanos, como `passouNoExameDoDetran`, não precisamos igualar a true/false, ou seja, não precisamos fazer `passouNoExameDoDetran == true`, porque só de colocarmos `passouNoExameDoDetran` ele já verifica se é verdadeiro. Para verificar se é falso, é só negar esse valor com o ponto de exclamação: `!passouNoExameDoDetran`.

### If / else if / else

O `else if` cria uma outra condição a ser testada logo após o if. Veja um exemplo abaixo:

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

Podemos ter diversos `else-if` encadeados.

### Operador ternário

O operador ternário é um modo mais curto e mais simples de executar um `if-else`. Veja um exemplo abaixo:
```swift
let idade = 20

idade >= 18 ? print("Pode dirigir") : print("Não pode dirigir")
```

Basicamente esse operador faz uma "pergunta". A idade é maior ou igual que 18? Se sim, executa a primeira instrução. Se não executa a segunda, o que vem depois dos dois pontos.

## Loops
Loops são um modo de executar código múltiplas vezes, ou seja, repetindo um bloco de código até uma condição de parada. 

Vamos supor que você esteja adoçando um café. Você coloca mais açúcar/adoçante **até que** o gosto esteja bom o suficiente para seu paladar, certo?

Então o fluxo é basicamente esse: coloca açúcar/adoçante -> mexe -> verifica se o gosto está bom -> se estiver, para de adoçar -> se não estiver, repete todo o processo.

Isso é um loop, e na programação eles são muito utilizados. Veja abaixo dois comandos que nos permitem lidar com esse fluxo:

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
    print(count)
}
```

O que acontece no código acima é que quando count for igual a 5, ele não será printado na tela, porque a palavra `continue` força a próxima iteração do loop.