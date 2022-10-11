# Variáveis

Variável é um espaço de memória usado para armazenar algum dado no nosso código.

Para declarar uma variável no Swift, usamos a palavra-chave `var`. Podemos também declarar uma constante, o que significa que seu valor não pode ser alterado, usando a palavra-chave `let`.

```swift
    var number = 10
    number = 8
```

```swift
    let number = 10
    // number = 8 (constantes não podem ser alteradas) 
```

O Swift é uma **linguagem fortemente tipada**, o que significa que se você criar uma variável do tipo número, não pode alterar posteriormente para outro tipo, por exemplo String.

Podemos também tornar de forma explícita qual o tipo de dado que estamos declarando nessa variável.

```swift
    var number: Int = 10
    var decimalNumber: Double = 10.5
    var name: String = "Giovanna"
```

Se você não declarar o tipo, o Swift consegue inferir implicitamente qual o tipo de dado você está atribuindo àquela variável, como no primeiro exemplo dado aqui.

E no caso de criar uma variável sem atribuir nenhum valor, ou seja, sem inicializá-la, você precisa explicitamente especificar o tipo de dado que será armazenado, veja o exemplo abaixo:

```swift
    // var number -> erro! precisa especificar seu tipo
    var number: Int
    number = 8
```

## A importância de usar nomes significativos

Para manter um código limpo e legível, é importante escolher bons nomes para variáveis, funções, classes, entre outros. Boa nomenclatura age como documentação e torna o código fácil para leitura. 

Um bom nome descreve especificamente o papel daquilo que está sendo criado, exemplo: `personAge`, `numberOfPeople`, `gradeAverage`. Um exemplo de uma variável não nomeada corretamente seria: `a`, `temp`, `average`.

A chave é garantir que você e outra pessoa irão entender o código em um futuro.




