# Mais funcionalidades sobre classes

No material anterior, falei da possibilidade de classes poder herdar de outras classes, um conceito muito presente na programação orientada a objetos. Vamos ver a seguir outras funcionalidades que classes podem oferecer:

## Herança

Em alguns casos, podemos ter duas classes que são extremamente parecidas. Por exemplo, uma classe que representa uma pessoa e outra classe que representa um estudante. 

Porém, todo estudante é uma pessoa, certo? Afinal ele também possui propriedades em comum como nome, sobrenome, idade.. E possui algumas informações específicas em relação a estudante, como um array que mostra suas notas, por exemplo.

Veja o exemplo abaixo:

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

class Student {
    let name: String
    let surname: String
    let age: Int
    var grades: [Double] = [] // já estamos inicializando essa variável (um array vazio), portanto não precisamos passar essa informação no construtor (init)

    init(name: String, surname: String, age: Int) {
        self.name = name
        self.surname = surname
        self.age = age
        self.grades = grades
    }

    func printGrades() {
        grades.forEach { grade in
            print(grade)
        }
    }

    func saySomething(sentence: String) {
        print(sentence)
    }
}
```

Se criarmos uma classe específica para pessoa e outra específica para estudante, há a redundância de informações. Muito código repetido, o que não entra em conformação com boas práticas. O ideal nesse caso é **herdar** informações.

Como todo estudante é uma pessoa, podemos dizer que a classe `Student` herda de `Person`:

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

class Student: Person {
    var grades: [Double] = []

    func printGrades() {
        grades.forEach { grade in
            print(grade)
        }
    }
}
```

Perceba que agora, `Student` herda todas as informações de `Person` e mantém apenas as informações que são exclusivas.

Para instanciar um objeto `Student`, precisamos passar as informações que estão no construtor de `Person`:

```swift
let student = Student(name: "Giovanna", surname: "Moeller", age: 21)
print(student.name) // "Giovanna"
print(student.grades) // []
```

E obviamente, se criarmos uma instância de `Person` e tentar acessar a variável `grades`, isso não é possível, pois a variável `grades` só existe na classe `Student`:

```swift
let student = Person(name: "Giovanna", surname: "Moeller", age: 21)
print(student.name) // "Giovanna"
print(student.grades) // erro!
```

Em termos técnicos, `Person` é uma superclasse (classe base), enquanto `Student` é uma subclasse (classe derivada).

**É importante ressaltar que uma classe pode herdar de apenas uma única classe** e que não há limite para a profundidade da subclasse, o que significa que você pode herdar de uma classe
que também é uma subclasse.

## Polimorfismo

A relação Aluno/Pessoa demonstra um conceito de ciência da computação conhecido como **polimorfismo**. Em resumo, o polimorfismo é a capacidade de uma linguagem de programação de tratar um objeto de maneira diferente com base no contexto.

Um estudante é, obviamente, um estudante, mas também é uma pessoa. Como ele deriva de `Person`, você pode usar o objeto `student` (a variável que instancia `Student`) em qualquer lugar que usar um objeto `Person`.

Veja um exemplo abaixo:

```swift
func sayHello(to person: Person) {
    print("Hello, \(person.name)!")
}
let student = Student(name: "Giovanna", surname: "Moeller", age: 21)
sayHello(to: student)
```

Pelo fato de um estudante ser uma pessoa, o código acima é válido.

## Override

E se quisermos sobrescrever um método existente na classe pai para a classe filha?

Vamos supor que queremos que o corpo da função `saySomething()` seja diferente na classe `Person` e na classe `Student`.

Podemos usar uma palavra-chave chamada de `override`, que significa sobreescrita:

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

class Student: Person {
    var grades: [Double] = []

    func printGrades() {
        grades.forEach { grade in
            print(grade)
        }
    }

    override func saySomething(sentence: String) {
        print("Um estudante disse: \(sentence)")
    }
}
```

## Super

Mas, se você quiser que ele ainda chame o método da classe pai e apenas depois execute algo definido pela subclasse, você pode chamar esse método através de uma palavra-chave denominada `super`:

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

class Student: Person {
    var grades: [Double] = []

    func printGrades() {
        grades.forEach { grade in
            print(grade)
        }
    }

    override func saySomething(sentence: String) {
        super.saySomething(sentence: sentence)
        print("Um estudante disse: \(sentence)")
    }
}
```

O resultado disso será:

```swift
let student = Student(name: "Giovanna", surname: "Moeller", age: 21)
student.saySomething(sentence: "Oie!")
/*
Oie!
Um estudante disse: Oie!
*/
```

A palavra-chave `super` é semelhante a `self`, exceto que invocará o método na superclasse.

Como você pode ter notado, aonde chamamos o `super` pode alterar o funcionamento do seu código. No exemplo abaixo, executará primeiro o "Um estudante disse: ", e depois executará o que está no método da classe pai.

```swift
class Student: Person {
    var grades: [Double] = []

    func printGrades() {
        grades.forEach { grade in
            print(grade)
        }
    }

    override func saySomething(sentence: String) {
        print("Um estudante disse: \(sentence)")
        super.saySomething(sentence: sentence)
    }
}
```

Veja que na nossa classe `Student` não temos um inicializador, mas poderíamos criar um passando a propriedade `grades`:

```swift
class Student: Person {
    var grades: [Double]
    
    init(grades: [Double]) {
        self.grades = grades
    }
}
```

O código acima causará um erro, porque é como se estivéssemos sobrescrevendo o `init` do `Person()`, então como obter as propriedades `name`, `surname` e `age`, que são necessárias?

```swift
class Student: Person {
    var grades: [Double]
    
    init(name: String, surname: String, age: Int, grades: [Double]) {
        self.grades = grades
        super.init(name: name, surname: surname, age: age)
    }
}

let student = Student(name: "Giovanna", surname: "Moeller", age: 21, grades: [8.0, 9.5, 8.8, 10.0, 9.3])
```

Podemos chamar o construtor de `Person` usando o `super.init()` e passando as informações necessárias.

**O `super.init()` deve ser chamado após você inicializar todas as suas variáveis ​​de instância.**

## Prevenir herança

Para prevenir que uma classe seja herdada, utilizamos a palavra-chave `final`, veja o exemplo abaixo:

```swift
final class Person {
}

class Student: Person { // erro! A classe Person não pode ser herdada
}
```