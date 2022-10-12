# Structures

Agora, vamos entrar em um outro tópico muito importante: os tipos que você mesmo irá definir.

Structures são tipos que podem armazenar propriedades e métodos que estão relacionadas.

Aqui entra muito o conceito de orientação a objetos. No Swift, `struct` e `class` são extremamente parecidos e vamos entender suas diferenças mais pra frente.

Vamos supor que queremos representar uma pessoa no nosso código. Uma pessoa possui características únicas como nome, sobrenome, idade, altura.. E também métodos em comum, como falar, comer, andar...

Então vamos criar uma estrutura que represente uma pessoa:

```swift
struct Person {
    let name: String
    let surname: String
    let age: Int

    func saySomething(sentence: String) {
        print(sentence)
    }
}
```

As variáveis `name`, `surname` e `age` são o que chamamos de propriedades, enquanto a função `saySomething` é o que chamamos de método.

Agora, vamos instanciar essa estrutura criando um objeto real para esse tipo:

```swift
struct Person {
    let name: String
    let surname: String
    let age: Int

    func saySomething(sentence: String) {
        print(sentence)
    }
}

let person1 = Person(name: "Giovanna", surname: "Moeller", age: 21)
person1.saySomething(sentence: "Hello, World!")
```

Ou, podemos instanciar dessa maneira, declarando o tipo explicitamente e utilizando o construtor:

```swift
let person1: Person = .init(name: "Giovanna", surname: "Moeller", age: 21)
```

Perceba que o `struct` não precisa de um inicializador, já é automático! Inicializador é um modo de forçar que todas as propriedades estejam setadas antes de utilizá-las. 

Para acessar as propriedades, usamos a sintaxe do ponto:

```swift
let person1 = Person(name: "Giovanna", surname: "Moeller", age: 21)
print(person1.name)
person1.saySomething(sentence: "Hello, World!")
```

Como declaramos `person1` como `let`, e também `name` como `let` não podemos alterar uma propriedade:

```swift
let person1 = Person(name: "Giovanna", surname: "Moeller", age: 21)
person1.name = "Gi"
person1.saySomething(sentence: "Hello, World!")
```

Para alterar uma propriedade, ela precisa ser declarada como `var` dentro da struct, e sua instância também precisa ser declarada como `var`.

Agora que você já sabe definir seu próprio tipo customizado, você pode fazer o que quiser com ele, como por exemplo, passar como parâmetro pra uma função:

```swift
func sayHello(to person: Person) {
    print("Hello, \(person.name)!")
}
let person1 = Person(name: "Giovanna", surname: "Moeller", age: 21)
sayHello(to: person1)
```