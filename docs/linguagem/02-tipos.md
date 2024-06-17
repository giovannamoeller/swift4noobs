# Tipos e Operações

## Tipos
Toda variável precisa ter um tipo. Tipos são o que definem o que aquele valor se refere. Por exemplo, um número inteiro será representado como `Int`, enquanto um decimal será `Double`. Um texto será uma `String` e um valor booleano será `Bool`.
```swift
var nome: String = "Giovanna"
var numero: Int = 8
var numeroDecimal: Double = 8.5
var adulto: Bool = true
```

Se declararmos uma variável e inicializarmos mas sem colocar explicitamente o seu tipo, o Swift saberá qual o tipo da variável por uma funcionalidade chamada de **"type inference"**, ou seja, inferência de tipo.

```swift
var nome = "Giovanna" // Swift sabe que isso é uma String
var numero = 8
var numeroDecimal = 8.5
var adulto = true
```

### Entendendo melhor sobre Strings

Strings são um conjunto de caracteres. No Swift, possuímos ambos os tipos: `Character` e `String`.
```swift
let caractereA: Character = "a" // se não especificar que é um character, o Swift entenderá que é uma string
let nome: String = "Giovanna"
```

Para concatenar duas ou mais strings, podemos fazer de duas maneiras:

```swift
let nome = "Giovanna"
var mensagem = "Meu nome é " + nome + "!"
```

Ou, de um modo mais fácil:

```swift
let nome = "Giovanna"
var mensagem = "Meu nome é \(nome)!"
```

No Swift, o uso de strings precisa ser feito através de aspas duplas. Aspas simples não são válidas.

### Typealias
É uma funcionalidade interessante da linguagem em que você pode criar seu próprio tipo que é um alias de outro tipo. O que isso significa que você pode fazer é dar um nome mais útil ao seu tipo que descreve o que é, mas por baixo, é apenas outro tipo. Exemplo:

```swift
typealias Animal = String
let meuPet: Animal = "Meu cachorro"
```

Esses tipos que você viu acima, como `Int`, `Float`, `Double`, `Bool`, `String`, são chamados de tipos básicos de uma linguagem.

Em breve, você verá sobre os tipos que representam uma coleção de dados, que é o caso do *Array*, *Set*, *Tuplas* e *Dicionários*. Eu não abordei esses tipos no momento porque acredito que faz mais sentido vermos eles mais pra frente, quando já aprendemos sobre funções e controle de fluxo.

Você verá também como criar o seu próprio tipo com o uso de classes, utilizando o princípio da orientação a objetos.

Ir para a próxima página: [03 - Operações](03-operacoes.md)