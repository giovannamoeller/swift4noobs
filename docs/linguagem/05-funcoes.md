# Funções

Funções possuem uma responsabilidade essencial nas linguagens de programação. Uma função define um bloco de código que realiza alguma função. Esse código pode ser reutilizado diversas vezes, basta chamar a função para isso.

## Declarando uma função

Para declarar uma função, precisamos da palavra-chave `func` e o nome da função, seguido de parênteses. Veja o código abaixo:

```swift
func printName() {
    print("Meu nome é Giovanna")
}
```

E então, para chamar essa função:

```swift
printName()
```

## Parâmetros de uma função

Uma função pode receber valores, chamados de parâmetros. Esses parâmetros precisam ter o seu tipo declarado de forma explícita. Veja o código abaixo:

```swift
func printName(name: String) {
    print("Meu nome é \(name)")
}

printName(name: "Giovanna") // precisamos especificar o parâmetro na chamada também
```

Podemos ter mais de um parâmetro na função:

```swift
func printName(name: String, age: Int) {
    print("Meu nome é \(name) e eu tenho \(age) anos")
}

printName(name: "Giovanna", age: 21) 
```

Mas, se você não quiser especificar o parâmetro quando está **chamando** a função, basta colocar um underline (_) na declaração do parâmetro, antes do seu próprio nome. Veja um exemplo abaixo:

```swift
func printName(_ name: String, _ age: Int) {
    print("Meu nome é \(name) e eu tenho \(age) anos")
}

printName("Giovanna", 21) 
```

Da mesma forma que podemos omitir o nome externo da variável, podemos alterar o nome que a referenciamos quando chamamos. Veja:

```swift
func printName(myName name: String) {
    print("Meu nome é \(name)") // aqui usamos name
}

printName(myName: "Giovanna") // aqui usamos myName 
```

Podemos também fornecer valores padrões (default) para os parâmetros:

```swift
func printName(name: String = "Giovanna") {
    print("Meu nome é \(name)")
}

printName() // como não passamos nada, será usado o "Giovanna"
```

## Retorno de valores

Uma função pode retornar um valor. Esse retorno precisa ter o seu tipo explícito e funciona dessa maneira:

```swift
func sum(_ number1: Int, _ number2: Int) -> Int {
    return number1 + number2
}

sum(3, 5)
```

Como nossa função possui apenas uma linha e é um retorno, podemos simplesmente omitir a palavra `return`.

## Parâmetros avançados

No Swift, um valor passado como parâmetro não pode ter seu valor alterado, porque funciona como constantes.

```swift
func increment(number: Int) {
    number += 1 // isso causará um erro pois number atua como 'let'
    print(number)
}

increment(number: 2)
```

Existe uma maneira de alterarmos esse comportamento, que é utilizar o que chamamos de passagem de valor por referência. Basicamente, não passamos uma cópia do valor para a função, mas sim o seu endereço de memória.

```swift
func increment(_ number: inout Int) {
    number += 1
    print(number)
}

var value = 2
increment(&value)
```

A palavra chave `inout` indica que esse parâmetro deve ser copiado, essa cópia local usada dentro da função e copiada de volta quando a função retornar. Perceba também que omitimos o nome do parâmetro na chamada da função e criamos uma variável para armazenar esse valor, passando com o símbolo & antes, que significa que estamos passando o endereço de memória.

## Funções como variáveis

Podemos atribuir funções a variáveis e também passar funções como argumentos de outra função. Aqui entra um conceito de **high order functions**, ou também **closures**, que será abordado de forma mais profunda mais pra frente. Mas, como conteúdo introdutório para esse assunto, veja o código abaixo:

```swift
func add(_ a: Int, _ b: Int) -> Int {
    a + b
}

var function = add // type inference, o Swift sabe que seu tipo é: (Int, Int) -> Int
function(2, 4) // 6
```

Agora, passando uma função como parâmetro de uma outra função:

```swift
func add(_ a: Int, _ b: Int) -> Int {
    a + b
}
func printResult(_ function: (Int, Int) -> Int, _ a: Int, _ b: Int) {
    let result = function(a, b)
    print(result)
}
printResult(add, 4, 2)
```

Vamos entender o que está acontecendo aqui: A função `printResult` recebe três parâmetros, primeiro, uma função que possui dois parâmetros inteiros e retorna um inteiro, segundo, um valor inteiro e terceiro, um outro valor inteiro.

Passamos como argumento pra essa função a outra função `add`, que possui o mesmo tipo que a função da função `printResult` precisa (pode ter ficado meio confuso isso hahahah), e então dois valores como 4 e 2.

Para tornar um pouco mais legível, podemos usar o `typealias` que vimos anteriormente em outro material:

```swift
func add(_ a: Int, _ b: Int) -> Int {
    a + b
}

typealias functionType = (Int, Int) -> Int

func printResult(_ function: functionType, _ a: Int, _ b: Int) {
    let result = function(a, b)
    print(result)
}
printResult(add, 4, 2)
```