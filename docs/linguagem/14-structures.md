# Structures

Agora, vamos entrar em um outro tópico muito importante: os tipos que você mesmo irá definir.

Structures são tipos que podem armazenar propriedades e métodos que estão relacionadas.

Aqui entra muito o conceito de orientação a objetos. No Swift, `struct` e `class` são extremamente parecidos e vamos entender suas diferenças mais pra frente.

Vamos supor que queremos representar uma pessoa no nosso código. Uma pessoa possui características únicas como nome, sobrenome, idade, altura.. E também métodos em comum, como falar, comer, andar...

Então vamos criar uma estrutura que represente uma pessoa:

```swift
struct Pessoa {
    let nome: String
    let sobrenome: String
    let idade: Int

    func falarAlgo(mensagem: String) {
        print(mensagem)
    }
}
```

As variáveis `nome`, `sobrenome` e `idade` são o que chamamos de propriedades, enquanto a função `falarAlgo` é o que chamamos de método.

Agora, vamos instanciar essa estrutura criando um objeto real para esse tipo:

```swift
struct Pessoa {
    let nome: String
    let sobrenome: String
    let idade: Int

    func falarAlgo(mensagem: String) {
        print(mensagem)
    }
}

let pessoa1 = Pessoa(nome: "Giovanna", sobrenome: "Moeller", idade: 21)
pessoa1.falarAlgo(mensagem: "Hello, World!")
```

Ou, podemos instanciar dessa maneira, declarando o tipo explicitamente e utilizando o construtor:

```swift
let pessoa1: Pessoa = .init(nome: "Giovanna", sobrenome: "Moeller", idade: 21)
// ou
let pessoa1 = Pessoa.init(nome: "Giovanna", sobrenome: "Moeller", idade: 21)
```

Perceba que o `struct` não precisa de um inicializador, já é automático! Inicializador é um modo de forçar que todas as propriedades estejam setadas antes de utilizá-las. Mas se você quiser criar um para customizar algo, é totalmente possível.

Para acessar as propriedades, usamos a sintaxe do ponto:

```swift
let pessoa1 = Pessoa(nome: "Giovanna", sobrenome: "Moeller", idade: 21)
print(pessoa1.nome)
pessoa1.falarAlgo(mensagem: "Hello, World!")
```

Como declaramos `pessoa1` como `let`, e também `nome` como `let` não podemos alterar uma propriedade:

```swift
let pessoa1 = Pessoa(nome: "Giovanna", sobrenome: "Moeller", idade: 21)
pessoa1.nome = "Gi"
pessoa1.falarAlgo(mensagem: "Hello, World!")
```

Para alterar uma propriedade, ela precisa ser declarada como `var` dentro da struct, e sua instância também precisa ser declarada como `var`.

Agora que você já sabe definir seu próprio tipo customizado, você pode fazer o que quiser com ele, como por exemplo, passar como parâmetro pra uma função:

```swift
func cumprimentar(_ pessoa: Pessoa) {
    print("Oie, \(pessoa.nome)!")
}
let pessoa1 = Pessoa(nome: "Giovanna", sobrenome: "Moeller", idade: 21)
cumprimentar(pessoa1)
```

Ir para a próxima página: [Classes](15-classes.md)