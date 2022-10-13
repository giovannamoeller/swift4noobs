# Mais funcionalidades sobre classes

No material anterior, falei da possibilidade de classes poder herdar de outras classes, um conceito muito presente na programação orientada a objetos. Vamos ver a seguir outras funcionalidades que classes podem oferecer:

## Herança

Em alguns casos, podemos ter duas classes que são extremamente parecidas. Por exemplo, uma classe que representa uma pessoa e outra classe que representa um estudante. 

Porém, todo estudante é uma pessoa, certo? Afinal ele também possui propriedades em comum como nome, sobrenome, idade.. E possui algumas informações específicas em relação a estudante, como um array que mostra suas notas, por exemplo.

Veja o exemplo abaixo:

```swift
class Pessoa {
    let nome: String
    let sobrenome: String
    let idade: Int

    init(nome: String, sobrenome: String, idade: Int) {
        self.nome = nome
        self.sobrenome = sobrenome
        self.idade = age
    }

    func falarAlgo(mensagem: String) {
        print(mensagem)
    }
}

class Estudante {
    let nome: String
    let sobrenome: String
    let idade: Int
    var notas: [Double] = [] // já estamos inicializando essa variável (um array vazio), portanto não precisamos passar essa informação no construtor (init)

    init(nome: String, sobrenome: String, idade: Int) {
        self.nome = nome
        self.sobrenome = sobrenome
        self.idade = idade
        self.notas = notas
    }

    func mostrarNotas() {
        notas.forEach { nota in
            print(nota)
        }
    }

    func falarAlgo(mensagem: String) {
        print(mensagem)
    }
}
```

Se criarmos uma classe específica para pessoa e outra específica para estudante, há a redundância de informações. Muito código repetido, o que não entra em conformação com boas práticas. O ideal nesse caso é **herdar** informações.

Como todo estudante é uma pessoa, podemos dizer que a classe `Estudante` herda de `Pessoa`:

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

class Estudante: Pessoa {
    var notas: [Double] = []

    func mostrarNotas() {
        notas.forEach { nota in
            print(nota)
        }
    }
}
```

Perceba que agora, `Estudante` herda todas as informações de `Pessoa` e mantém apenas as informações que são exclusivas.

Para instanciar um objeto `Estudante`, precisamos passar as informações que estão no construtor de `Pessoa`:

```swift
let estudante = Estudante(nome: "Giovanna", sobrenome: "Moeller", idade: 21)
print(estudante.nome) // "Giovanna"
print(estudante.notas) // []
```

E obviamente, se criarmos uma instância de `Pessoa` e tentar acessar a variável `notas`, isso não é possível, pois a variável `notas` só existe na classe `Estudante`:

```swift
let estudante = Pessoa(nome: "Giovanna", sobrenome: "Moeller", idade: 21)
print(estudante.nome) // "Giovanna"
print(estudante.notas) // erro!
```

Em termos técnicos, `Pessoa` é uma superclasse (classe base), enquanto `Estudante` é uma subclasse (classe derivada).

**É importante ressaltar que uma classe pode herdar de apenas uma única classe** e que não há limite para a profundidade da subclasse, o que significa que você pode herdar de uma classe
que também é uma subclasse.

## Polimorfismo

A relação Aluno/Pessoa demonstra um conceito de ciência da computação conhecido como **polimorfismo**. Em resumo, o polimorfismo é a capacidade de uma linguagem de programação de tratar um objeto de maneira diferente com base no contexto.

Um estudante é, obviamente, um estudante, mas também é uma pessoa. Como ele deriva de `Pessoa`, você pode usar o objeto `estudante` (a variável que instancia `Estudante`) em qualquer lugar que usar um objeto `Pessoa`.

Veja um exemplo abaixo:

```swift
func cumprimentar(_ pessoa: Pessoa) {
    print("Olá, \(pessoa.nome)!")
}
let estudante = Estudante(nome: "Giovanna", sobrenome: "Moeller", idade: 21)
cumprimentar(to: estudante)
```

Pelo fato de um estudante ser uma pessoa, o código acima é válido.

## Override

E se quisermos sobrescrever um método existente na classe pai para a classe filha?

Vamos supor que queremos que o corpo da função `falarAlgo()` seja diferente na classe `Pessoa` e na classe `Estudante`.

Podemos usar uma palavra-chave chamada de `override`, que significa sobreescrita:

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

class Estudante: Pessoa {
    var notas: [Double] = []

    func mostrarNotas() {
        notas.forEach { nota in
            print(nota)
        }
    }

    override func falarAlgo(mensagem: String) {
        print("Um estudante disse: \(mensagem)")
    }
}
```

## Super

Mas, se você quiser que ele ainda chame o método da classe pai e apenas depois execute algo definido pela subclasse, você pode chamar esse método através de uma palavra-chave denominada `super`:

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

class Estudante: Pessoa {
    var notas: [Double] = []

    func mostrarNotas() {
        notas.forEach { nota in
            print(nota)
        }
    }

    override func falarAlgo(mensagem: String) {
        super.falarAlgo(mensagem: mensagem)
        print("Um estudante disse: \(mensagem)")
    }
}
```

O resultado disso será:

```swift
let estudante = Estudante(nome: "Giovanna", sobrenome: "Moeller", idade: 21)
estudante.falarAlgo(mensagem: "Oie!")
/*
Oie!
Um estudante disse: Oie!
*/
```

A palavra-chave `super` é semelhante a `self`, exceto que invocará o método na superclasse.

Como você pode ter notado, aonde chamamos o `super` pode alterar o funcionomento do seu código. No exemplo abaixo, executará primeiro o "Um estudante disse: ", e depois executará o que está no método da classe pai.

```swift
class Estudante: Pessoa {
    var notas: [Double] = []

    func mostrarNotas() {
        notas.forEach { nota in
            print(nota)
        }
    }

    override func falarAlgo(mensagem: String) {
        print("Um estudante disse: \(mensagem)")
        super.falarAlgo(mensagem: mensagem)
    }
}
```

Veja que na nossa classe `Estudante` não temos um inicializador, mas poderíamos criar um passando a propriedade `notas`:

```swift
class Estudante: Pessoa {
    var notas: [Double]
    
    init(notas: [Double]) {
        self.notas = notas
    }
}
```

O código acima causará um erro, porque é como se estivéssemos sobrescrevendo o `init` do `Pessoa()`, então como obter as propriedades `nome`, `sobrenome` e `idade`, que são necessárias?

```swift
class Estudante: Pessoa {
    var notas: [Double]
    
    init(nome: String, sobrenome: String, idade: Int, notas: [Double]) {
        self.notas = notas
        super.init(nome: nome, sobrenome: sobrenome, idade: idade)
    }
}

let estudante = Estudante(nome: "Giovanna", sobrenome: "Moeller", idade: 21, notas: [8.0, 9.5, 8.8, 10.0, 9.3])
```

Podemos chamar o construtor de `Pessoa` usando o `super.init()` e passando as informações necessárias.

**O `super.init()` deve ser chamado após você inicializar todas as suas variáveis ​​de instância.**

## Prevenir herança

Para prevenir que uma classe seja herdada, utilizamos a palavra-chave `final`, veja o exemplo abaixo:

```swift
final class Pessoa {
}

class Estudante: Pessoa { // erro! A classe Pessoa não pode ser herdada
}
```

Ir para a próxima página: [Propriedades](docs/linguagem/18-propriedades.md)
