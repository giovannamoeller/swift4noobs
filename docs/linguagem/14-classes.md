# Classes

Como já havia comentado anteriormente, classes são extremamente parecidas com structures. Seguindo o mesmo exemplo anterior, vamos criar uma classe que representa uma pessoa, com suas propriedades e métodos:

```swift
class Person {
    let name: String
    let surname: String
    let age: Int

    init(name: String, surname: String, age: Int) {
        self.name = name
        self.surname = surname
        self.age = age
    }

    func saySomething(sentence: String) {
        print(sentence)
    }
}
let person1 = Person(name: "Giovanna", surname: "Moeller", age: 21)
```

Perceba que agora criamos um inicializador, pois em classes eles são necessários.

Da mesma maneira que `struct` possui suas propriedades e métodos, classes também possuem. Mas então, quais as diferenças práticas entre eles? Vamos ver mais sobre isso no próximo material!