# Protocolos

Protocolo nada mais é do que um **conjunto de regras** que precisam ser seguidas. É uma funcionalidade muito interessante da linguagem.

Ao contrário dos outros tipos nomeados, os protocolos não podem ser instanciados, porque eles não definem nada concreto. Em vez disso, eles definem uma **interface** para que os tipos concretos (como classes e structures) entrem em conformidade. 

Com um protocolo, você define um conjunto comum de propriedades e comportamentos para que esses tipos implementem.

Um fato curioso é que o Swift é a primeira linguagem orientada a protocolos e há o grande incentivo de você desenvolver dessa forma.

## Criando um protocolo

Vamos definir um procolo abaixo:

```swift
protocol Veiculo {
    func acelerar()
    func parar()
}
```

O que está acontecendo acima é simples: um veículo pode acelerar e parar.

Agora, vamos criar uma `struct` que representa um carro. Um carro é um veículo, então ele precisa implementar os métodos de acelerar e parar:

```swift
class Carro: Veiculo {
    func acelerar() {
        print("Carro está acelerando!")
    }
    func parar() {
        print("Carro está parado.")
    }
}
```

Veja só: nossa classe `Carro` está em conformidade com o protocolo `Veiculo`. Caso a gente especifique que precisa estar em conformidade mas não implementa os métodos necessários, causará um erro na nossa aplicação: "Type 'Carro' does not conform to protocol 'Veiculo'".

Um protocolo pode ser adotado por uma classe, structure, enumeration ou até mesmo uma extension.

Os métodos dentro do protocolo precisam definir bem o que será passado de parâmetro e qual será o seu retorno. Além disso, o protocolo também pode definir propriedades.

Veja mais um exemplo abaixo:

```swift
enum Direcao {
    case esquerda
    case direita
}

protocol Veiculo {
    func acelerar()
    func parar()
    func virar(_ direcao: Direcao)
    func descricaoDoVeiculo() -> String

    var peso: Int { get }
    var nome: String { get set }
}
```

Quando definimos propriedades em protocolos, precisamos especificar se elas são apenas de **leitura** (*get*) ou de **escrita** também (*get set*).

Uma outra funcionalidade interessante é que também há herança em protocolos. Veja o exemplo abaixo:

```swift
enum Direcao {
    case esquerda
    case direita
}

protocol PropriedadesVeiculo {
    var peso: Int { get }
    var nome: String { get set }
}

protocol Veiculo: PropriedadesVeiculo {
    func acelerar()
    func parar()
    func virar(_ direcao: Direcao)
    func descricaoDoVeiculo() -> String
}
```

Veja que separamos as propriedades em um outro protocolo chamado `PropriedadesVeiculo`. Caso o nosso tipo (Carro) conforme ao protocolo `Veiculo`, ele precisará adicionar as propriedades também, pois `Veiculo` herda de `PropriedadesVeiculo`.

Uma classe pode apenas herdar de uma única classe. Lembra disso? Com protocolos isso não acontece! Uma classe, structure enumeration e até mesmo extensions pode conformar vários protocolos ao mesmo tempo.

Ir para a próxima página: [Generics](22-generics.md)