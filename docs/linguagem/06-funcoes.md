# Funções

Funções possuem uma responsabilidade essencial nas linguagens de programação. Uma função define um bloco de código que realiza alguma função. Esse código pode ser reutilizado diversas vezes, basta chamar a função para isso.

## Declarando uma função

Para declarar uma função, precisamos da palavra-chave `func` e o nome da função, seguido de parênteses. Veja o código abaixo:

```swift
func printaNome() {
    print("Meu nome é Giovanna")
}
```

E então, para chamar essa função:

```swift
printaNome()
```

## Parâmetros de uma função

Uma função pode receber valores, chamados de parâmetros. Esses parâmetros precisam ter o seu tipo declarado de forma explícita. Veja o código abaixo:

```swift
func printaNome(nome: String) {
    print("Meu nome é \(nome)")
}

printaNome(nome: "Giovanna") // precisamos especificar o parâmetro na chamada também
```

Podemos ter mais de um parâmetro na função:

```swift
func printaNome(nome: String, idade: Int) {
    print("Meu nome é \(nome) e eu tenho \(idade) anos")
}

printaNome(nome: "Giovanna", idade: 21) 
```

Mas, se você não quiser especificar o parâmetro quando está **chamando** a função, basta colocar um underline (_) na declaração do parâmetro, antes do seu próprio nome. Veja um exemplo abaixo:

```swift
func printaNome(_ nome: String, _ idade: Int) {
    print("Meu nome é \(nome) e eu tenho \(idade) anos")
}

printaNome("Giovanna", 21) 
```

Da mesma forma que podemos omitir o nome externo da variável, podemos alterar o nome que a referenciamos quando chamamos. Veja:

```swift
func printaNome(meuNome nome: String) {
    print("Meu nome é \(nome)") // aqui usamos nome
}

printaNome(meuNome: "Giovanna") // aqui usamos meuNome 
```

Podemos também fornecer valores padrões (default) para os parâmetros:

```swift
func printaNome(nome: String = "Giovanna") {
    print("Meu nome é \(nome)")
}

printaNome() // como não passamos nada, será usado o "Giovanna"
```

## Retorno de valores

Uma função pode retornar um valor. Esse retorno precisa ter o seu tipo explícito e funciona dessa maneira:

```swift
func sum(_ numero1: Int, _ numero2: Int) -> Int {
    return numero1 + numero2
}

sum(3, 5)
```

Como nossa função possui apenas uma linha e é um retorno, podemos simplesmente omitir a palavra `return`.

## Parâmetros avançados

No Swift, um valor passado como parâmetro não pode ter seu valor alterado, porque funciona como constantes.

```swift
func incremento(numero: Int) {
    numero += 1 // isso causará um erro pois numero atua como 'let'
    print(numero)
}

incremento(numero: 2)
```

Existe uma maneira de alterarmos esse comportamento, que é utilizar o que chamamos de passagem de valor por referência. Basicamente, não passamos uma cópia do valor para a função, mas sim o seu endereço de memória.

```swift
func incremento(_ numero: inout Int) {
    numero += 1
    print(numero)
}

var valor = 2
incremento(&valor)
```

A palavra chave `inout` indica que esse parâmetro deve ser copiado, essa cópia local usada dentro da função e copiada de volta quando a função retornar. Perceba também que omitimos o nome do parâmetro na chamada da função e criamos uma variável para armazenar esse valor, passando com o símbolo & antes, que significa que estamos passando o endereço de memória.

## Funções como variáveis

Podemos atribuir funções a variáveis e também passar funções como argumentos de outra função. Aqui entra um conceito de **high order functions**, ou também **closures**, que será abordado de forma mais profunda mais pra frente. Mas, como conteúdo introdutório para esse assunto, veja o código abaixo:

```swift
func adiciona(_ a: Int, _ b: Int) -> Int {
    a + b
}

var funcao = adiciona // type inference, o Swift sabe que seu tipo é: (Int, Int) -> Int
funcao(2, 4) // 6
```

Agora, passando uma função como parâmetro de uma outra função:

```swift
func adiciona(_ a: Int, _ b: Int) -> Int {
    a + b
}
func printaResultado(_ funcao: (Int, Int) -> Int, _ a: Int, _ b: Int) {
    let resultado = funcao(a, b)
    print(resultado)
}
printaResultado(adiciona, 4, 2)
```

Vamos entender o que está acontecendo aqui: A função `printaResultado` recebe três parâmetros, primeiro, uma função que possui dois parâmetros inteiros e retorna um inteiro, segundo, um valor inteiro e terceiro, um outro valor inteiro.

Passamos como argumento pra essa função a outra função `adiciona`, que possui o mesmo tipo que a função da função `printaResultado` precisa (pode ter ficado meio confuso isso hahahah), e então dois valores como 4 e 2.

Para tornar um pouco mais legível, podemos usar o `typealias` que vimos anteriormente em outro material:

```swift
func adiciona(_ a: Int, _ b: Int) -> Int {
    a + b
}

typealias tipoFuncao = (Int, Int) -> Int

func printaResultado(_ funcao: tipoFuncao, _ a: Int, _ b: Int) {
    let resultado = funcao(a, b)
    print(resultado)
}
printaResultado(adiciona, 4, 2)
```

Ir para a próxima página: [Opcionais](07-opcionais.md)