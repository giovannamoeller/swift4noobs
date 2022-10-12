# Propriedades

Vimos que podemos construir propriedades dentro de `struct` ou `class`.

Propriedades são características, atributos de um certo objeto.

Existem algumas propriedades que são diferentes de outras, vamos entender melhor a seguir:

## Stored Properties (propriedades armazenadas)

Você já está bem familiar com esse conceito porque uma *stored property* é uma propriedade comum que possui o seu tipo de dado:

```swift
struct Person {
    var name: String
    var surname: String
    var age: Int
}
```

Podemos também atribuir valores a essas propriedades depois de instanciadas:

```swift
var person = Person(name: "Giovanna", surname: "Moeller", age: 21)
person.age = 22
```

### Valores padrões (default)

Podemos oferecer valores chamados de `default` para as propriedades. Nesse caso, elas não precisam ser passadas pelo inicializador, porque já possuem um valor padrão:

```swift
struct Person {
    var name: String = "Giovanna"
    var surname: String = "Moeller"
    var age: Int = 20
}
var person = Person()
```

## Computed Properties (propriedades calculadas)

Algumas propriedades podem ser **computadas**, o que significa que elas realizam um **cálculo** antes de retornar um valor.

Enquanto uma propriedade armazenada pode ser uma constante ou uma variável, uma propriedade computada deve ser definida como uma variável.

Propriedades computadas também devem incluir um tipo porque o compilador precisa saber o que esperar como valor de retorno.

Veja um exemplo abaixo de propriedade computada:

```swift
struct Rectangle {
    var width: Double
    var height: Double

    var area: Double {
        return width * height
    }
}

var rectangle = Rectangle(width: 50.0, height: 70.0)
print(rectangle.area) // 3500
rectangle.width = 60.0
print(rectangle.area) // 4200
// rectangle.area = 5000 -> não é permitido setar uma propriedade computada, apenas ler o seu valor (get-only)
```

## Getter and Setter

A propriedade computada que você escreveu acima é chamada de *get-only*, porque apenas a sua leitura é permitida, a escrita não. 

Ele possui um bloco de código para calcular o valor da propriedade, chamado de *getter*.

Também é possível criar uma propriedade computada de leitura/escrita com dois blocos de código: um *getter* e um *setter*.

Este *setter* funciona de forma diferente do que você poderia esperar.
Como a propriedade computada não tem lugar para armazenar um valor, o setter geralmente define uma ou
mais propriedades armazenadas (*stored properties*):

```swift
class Weight {
    var kilograms: Float = 0.0
    var pounds: Float {
        get {
            return kilograms * 2.205
        }
        set(newWeight) {
            kilograms = newWeight / 2.205
        }
        /*
        set {
            kilograms = newValue / 2.205
        }
        */
    }
}

let weight = Weight()
weight.kilograms = 100
print(weight.pounds) // método get é invocado - 220.5
weight.pounds = 315 // método set é invocado
print(weight.kilograms) // 142.9
```

Veja que no `set` passamos um parâmetro chamado `newWeight`. Mas se não quiser passar um parâmetro, você ainda pode usar o `newValue` que automaticamente pega o novo valor, é uma funcionalidade do Swift pra você não se preocupar em passar os parâmetros:

```swift
class Weight {
    var kilograms: Float = 0.0
    var pounds: Float {
        get {
            return kilograms * 2.205
        }
        set {
            kilograms = newValue / 2.205
        }
    }
}
```

Lembrando que `get` e `set` são aplicados somente em propriedades computadas.

## Propriedades estáticas

Propriedades estáticas são propriedades que pertencem a clsse/struct, e não a sua instância. Elas são definidas pela palavra-chave `static`.

Veja um exemplo:

```swift
struct Network {
    static let APIUrl = "https://...."
}

let APIRequest = Network()
// não conseguimos acesso a propriedade APIUrl pela instância APIRequest, então precisamos acessar dessa maneira:
let APIUrl = Network.APIUrl
```

## Observadores de propriedade (property observers)
Esses observadores monitoram as alterações causadas em propriedades. Existem dois observadores: `willSet` e `didSet`.Esses métodos são chamados antes e depois de uma propriedade mudar.

Um observador `willSet` é chamado quando uma propriedade **está prestes a ser alterada**, enquanto um observador `didSet` é chamado **depois que uma propriedade foi alterada**. Sua sintaxe é semelhante a getters e setters:

### willSet

```swift
struct Rectangle {
    var width: Double {
        willSet { // se quiser usar um willSet(valorNovo), ou qualquer outro nome pra referenciar a variável nova, sem problemas!
            print("Width acabou de ser alterada. Seu novo valor é \(newValue)")
        }
    }
    var height: Double

    var area: Double {
        return width * height
    }
}

var rectangle = Rectangle(width: 50.0, height: 60.0)
rectangle.width = 60.0
// Width acabou de ser alterada. Seu novo valor é 60.0
```

Da mesma maneira que o `set` não precisa tomar como parâmetro um valor, o `willSet` e `didSet` também não. O `newValue` já está incluso e definido pela própria linguagem, ele pega o novo valor para que a propriedade foi alterada.

### didSet

```swift
struct Rectangle {
    var width: Double {
        didSet {
            print("Width acabou de ser alterada. Seu valor antigo era \(oldValue)")
        }
    }
    var height: Double

    var area: Double {
        return width * height
    }
}

var rectangle = Rectangle(width: 50.0, height: 60.0)
rectangle.width = 60.0
// Width acabou de ser alterada. Seu valor antigo era 50.0
```

O parâmetro `oldValue` em `didSet` é referente ao **valor antigo** da propriedade.

É legal usar observadores porque você pode pensar em várias lógicas na sua aplicação em relação a isso, como por exemplo pensar em uma forma de implementar o conceito de **estado**, chamar uma função novamente toda vez que uma propriedade é alterada.

Lembre-se de que os observadores `willSet` e `didSet` não são chamados quando uma propriedade é definida durante a inicialização; eles só são chamados quando você atribui um novo valor a uma instância totalmente inicializada.