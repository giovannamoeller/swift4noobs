# Variáveis

Variável é um espaço de memória usado para armazenar algum dado no nosso código.

Para declarar uma variável no Swift, usamos a palavra-chave `var`. Podemos também declarar uma constante, o que significa que seu valor não pode ser alterado, usando a palavra-chave `let`.

```swift
var numero = 10
numero = 8
```

```swift
let numero = 10
// numero = 8 (constantes não podem ser alteradas) 
```

O Swift é uma **linguagem fortemente tipada**, o que significa que se você criar uma variável do tipo número, não pode alterar posteriormente para outro tipo, por exemplo String.

Podemos também tornar de forma explícita qual o tipo de dado que estamos declarando nessa variável.

```swift
var numero: Int = 10
var numeroDecimal: Double = 10.5
var nome: String = "Giovanna"
```

Se você não declarar o tipo, o Swift consegue inferir implicitamente qual o tipo de dado você está atribuindo àquela variável, como no primeiro exemplo dado aqui.

E no caso de criar uma variável sem atribuir nenhum valor, ou seja, sem inicializá-la, você precisa explicitamente especificar o tipo de dado que será armazenado, veja o exemplo abaixo:

```swift
// var numero -> erro! precisa especificar seu tipo
var numero: Int
numero = 8
```

## A importância de usar nomes significativos

Para manter um código limpo e legível, é importante escolher bons nomes para variáveis, funções, classes, entre outros. Boa nomenclatura age como documentação e torna o código fácil para leitura. 

Um bom nome descreve especificamente o papel daquilo que está sendo criado, exemplo: `idadePessoa`, `numeroDePessoas`, `mediaDasNotas`. Um exemplo de uma variável não nomeada corretamente seria: `a`, `temp`, `media`.

A chave é garantir que você e outra pessoa irão entender o código em um futuro.

Ir para a próxima página: [02 - Tipos de dados](02-tipos.md)
