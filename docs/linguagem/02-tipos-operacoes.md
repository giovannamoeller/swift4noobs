# Tipos e Operações

## Tipos
Toda variável precisa ter um tipo. Tipos são o que definem o que aquele valor se refere. Por exemplo, um número inteiro será representado como `Int`, enquanto um decimal será `Double`. Um texto será uma `String` e um valor booleano será `Bool`.
```swift
var name: String = "Giovanna"
var number: Int = 8
var decimalNumber: Double = 8.5
var isAdult: Bool = true
```

Se declararmos uma variável e inicializarmos mas sem colocar explicitamente o seu tipo, o Swift saberá qual o tipo da variável por uma funcionalidade chamada de **"type inference"**, ou seja, inferência de tipo.

```swift
var name = "Giovanna" // Swift sabe que isso é uma String
var number = 8
var decimalNumber = 8.5
var isAdult = true
```

## Operações
Quando você pega um ou mais dados e os transforma em outro, isso é conhecido como uma operação. Dentro da programação, temos diversos tipos de operações:

### 1. Operações aritméticas
São operações conhecidas como soma (+), subtração (-), multiplicação (*), divisão (/) e módulo (%, representa o resto de uma divisão).

```swift
let sum = 2 + 6
let sub = 10 - 2
let multi = 2 * 4
let div = 24 / 3
let module = 4 % 2
```

Se você realizar uma divisão entre dois números inteiros, o resultado será um inteiro.

```swift
7 / 2 // resultado: 3
7.0 / 2.0 // resultado: 3.5
```

### 2. Ordem das operações
A ordem segue a mesma ordem da matemática: os parênteses possuem uma maior precedência, será executado primeiro. E então, operadores como divisão, multiplicação e módulo. Por fim, temos os outros operadores de soma e subtração.

```swift
350 / 5 + 2 // resultado: 72
350 / (5 + 2) // resultado: 50
```

### 3. Operadores de atribuição composta
Esses operadores são semelhantes ao operador de atribuição (=), exceto que também executam uma operação artimética. Eles pegam o valor atual da variável, realizam uma operação em cima do valor dado e atribua o resultado à variável.

```swift
var number = 10
number *= 3 // mesma coisa de number = number * 3
// number = 30
number /= 2
// number = 15
```

### 4. Operadores relacionais
Esses operadores comparam dois valores em determinada condição e retornam um valor booleano (verdadeiro ou falso).

```swift
3 == 2 // false
3 != 2 // true
3 > 3 // false
3 >= 3 // true
3 < 3 // false
3 <= 3 // true
```

### 5. Operadores lógicos
Esses operadores comparam duas condições e também retornam um valor booleano. Esses operadores são os mesmos da tabela verdade: AND (&&), OR (||) e NOT (!).

```swift
1 < 2 && 3 > 4 // false
1 < 2 || 3 > 4 // true
1 < 2 // true
!(1 < 2) // false
```

Lembrando que os parênteses aqui também indicam uma maior precedência em relação a operação.