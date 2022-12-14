# Operações
Quando você pega um ou mais dados e os transforma em outro, isso é conhecido como uma operação. Dentro da programação, temos diversos tipos de operações:

## 1. Operadores aritméticos
Operações aritméticas são conhecidas como soma (+), subtração (-), multiplicação (*), divisão (/) e módulo (%, representa o resto de uma divisão).

```swift
let soma = 2 + 6
let subtracao = 10 - 2
let multiplicacao = 2 * 4
let divisao = 24 / 3
let modulo = 4 % 2
```

Se você realizar uma divisão entre dois números inteiros, o resultado será um inteiro.

```swift
7 / 2 // resultado: 3
7.0 / 2.0 // resultado: 3.5
```

## 2. Ordem das operações
A ordem segue a mesma ordem da matemática: os parênteses possuem uma maior precedência, será executado primeiro. E então, operadores como divisão, multiplicação e módulo. Por fim, temos os outros operadores de soma e subtração.

```swift
350 / 5 + 2 // resultado: 72
350 / (5 + 2) // resultado: 50
```

## 3. Operadores de atribuição composta
Esses operadores são semelhantes ao operador de atribuição (=), exceto que também executam uma operação artimética. Eles pegam o valor atual da variável, realizam uma operação em cima do valor dado e atribua o resultado à variável.

```swift
var numero = 10
numero *= 3 // mesma coisa de numero = numero * 3
// numero = 30
numero /= 2
// numero = 15
```

## 4. Operadores relacionais
Esses operadores comparam dois valores em determinada condição e retornam um valor booleano (verdadeiro ou falso).

```swift
3 == 2 // false
3 != 2 // true
3 > 3 // false
3 >= 3 // true
3 < 3 // false
3 <= 3 // true
```

## 5. Operadores lógicos
Esses operadores comparam duas condições e também retornam um valor booleano. Esses operadores são os mesmos da tabela verdade: AND (&&), OR (||) e NOT (!).

```swift
1 < 2 && 3 > 4 // false
1 < 2 || 3 > 4 // true
1 < 2 // true
!(1 < 2) // false
```

Lembrando que os parênteses aqui também indicam uma maior precedência em relação a operação.

Ir para a próxima página: [Controle de fluxo básico](04-controle-fluxo-basico.md)