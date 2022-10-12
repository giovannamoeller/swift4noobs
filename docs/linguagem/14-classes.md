# Classes

Como já havia comentado anteriormente, classes são extremamente parecidas com structures. Seguindo o mesmo exemplo anterior, vamos criar uma classe que representa uma pessoa, com suas propriedades e métodos:

```swift
class Pessoa {
    let nome: String
    let sobrenome: String
    let idade: Int

    init(nome: String, sobrenome: String, idade: Int) {
        self.nome = nome
        self.sobrenome = sobrenome
        self.idade = idade
    }

    func falarAlgo(mensagem: String) {
        print(mensagem)
    }
}
let pessoa1 = Pessoa(nome: "Giovanna", sobrenome: "Moeller", idade: 21)
```

Perceba que agora criamos um inicializador, pois em classes eles são necessários.

Da mesma maneira que `struct` possui suas propriedades e métodos, classes também possuem. Mas então, quais as diferenças práticas entre eles? Vamos ver mais sobre isso no próximo material!