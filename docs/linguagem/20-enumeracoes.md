# Enumerations

Para começar a entender sobre *enumeration* (enumerações), vamos imaginar a seguinte situação:

Você tem uma função que recebe o estado atual de um semáforo, se ele está verde, amarelo ou vermelho.

A sua função pode ser escrita dessa maneira:

```swift
func checaSemaforo(estado: String) {
    switch estado {
        case "verde": print("Pode seguir!")
        case "vermelho": print("Fique parado!")
        case "amarelo": print("Atenção!")
        default: break
    }
}

checaSemaforo(estado: "verde")
```

Mas perceba que receber uma string não é tão seguro nesse caso, porque e se escrevermos errado, por exemplo? "verdee" em vez de "verde? Causa um erro inesperado. E se escrevermos com letra maiúscula? Como sabemos qual o certo?

É esse problema que *enumerations* resolve, pois ele cria um tipo que possui **vários casos**.

Uma enumeração é uma lista de valores relacionados que definem um tipo comum e permitem que você trabalhe com valores de maneira segura. O compilador detectará seu erro se seu código esperar um estado de um semáforo e você tentar passar em um número como 10 ou um estado com erros ortográficos como "verdee".

## Criando um enum

Veja o código abaixo:

```swift
enum Semaforo {
    case verde
    case vermelho
    case amarelo
}
```

Agora, não temos mais como errar na hora da escrita, pois temos casos únicos e específicos que estão relacionados entre si.

```swift 
func checaSemaforo(estado: Semaforo) {
    switch estado {
        case .verde: print("Pode seguir!")
        case .vermelho: print("Fique parado!")
        case .amarelo: print("Atenção!")
        default: break
    }
}

enum Semaforo {
    case verde
    case vermelho
    case amarelo
}

var verde = Semaforo.verde
checaSemaforo(estado: verde)
// ou, fazer dessa forma abaixo já é suficiente:
checaSemaforo(estado: .vermelho)
```

Outra vantagem de usar enumerações em vez de strings é que você nunca terá um erro de digitação em seus valores de membro. O Xcode fornece o que chamamos de *code completion*, uma funcionalidade de IDE's que te auxilia no desenvolvimento.

Um ponto interessante é que nem precisamos usar o `default` do `switch`, ele nunca será executado pois estamos cobrindo todos os casos do `enum` "Semaforo" dentro da condicional.

Enumerations são MUITO utilizados com a condicional `switch`, porque conseguimos abordar os dados de uma maneira bem simples e direta.

Vamos declarar mais um `enum`:

```swift
enum Mes {
    case janeiro
    case fevereiro
    case marco
    case abril
    case maio
    case junho
    case julho
    case agosto
    case setembro
    case outubro
    case novembro
    case dezembro
}
```

Podemos simplificar o `enum` acima utilizando vírgula entre os casos e removendo a palavra-chave `case` de todos, exceto do primeiro:

```swift
enum Mes {
    case janeiro, fevereiro, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
}
``` 

## Raw Values

Quando trabalhamos com os casos de um `enum`, podemos ter um valor que os representam. Esse valor pode ser um inteiro, uma string... Veja o código abaixo:

```swift
enum Mes: Int { // precisamos definir o tipo do raw value
    case janeiro, fevereiro, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
}

print(Mes.fevereiro.rawValue) // 1
print(Mes.setembro.rawValue) // 8
```

A contagem inicia no primeiro caso e no valor 0. Porém, podemos mudar isso:

```swift
enum Mes: Int {
    case janeiro = 5, fevereiro, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
}

print(Mes.fevereiro.rawValue) // 6
print(Mes.setembro.rawValue) // 13
```

Agora, defimos que o primeiro caso começará a partir da contagem em 5. O compilador incrementa automaticamente os valores a partir do valor que você determinou. Se você não determinou nenhum valor, como no primeiro caso, a contagem inicia em 0.

Se você utilizar *raw value* em formato de string, ele irá pegar a string literal de cada caso:

```swift
enum Mes: String {
    case janeiro, fevereiro, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
}

print(Mes.fevereiro.rawValue) // "fevereiro"
```

Lembrando que quando usamos inteiros como *raw values*, eles não precisam estar em ordem necessariamente. 

```swift
enum Moeda: Int {
    case 1centavo = 1
    case 5centavos = 5
    case 10centavos = 10
    case 25centavos = 25
    case 50centavos = 50
}
```

### Inicialização através do Raw Value

Você pode usar o *raw value* para instanciar um valor de enumeração com um inicializador.

```swift
enum Mes: Int {
    case janeiro = 1, fevereiro, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
}

let segundoMes = Mes(rawValue: 2) // fevereiro
```

## Associated values

Os valores associados levam as enumerações do Swift ao próximo nível. Eles permitem que você associe um valor (ou valores) personalizado a cada caso de enumeração.

Aqui estão algumas características de valores associados:
1. Cada caso de enumeração tem zero ou mais valores associados.
2. Os valores associados para cada caso de enumeração possuem seu próprio tipo de dados.
3. Você pode definir valores associados com nomes assim como faria para parâmetros de função. Vamos entender isso mais pra frente.

Uma enumeração pode ter *raw vales* ou *associated values*, mas não ambos.

Vamos supor a seguinte situação: você vai em um banco e tenta sacar um valor em dinheiro maior do que o que existe na sua conta. Isso não é possível, certo? Podemos criar um `enum` para lidar com isso:

```swift
enum ResultadoSaque {
    case sucesso(novoValor: Int)
    case erro(mensagem: String)
}
```

Perceba que cada caso possui um valor associado. 

Agora, podemos escrever uma função dessa maneira:

```swift
func saque(valor: Int) -> ResultadoSaque {
    if valor <= saldo {
        saldo -= valor
        return .sucesso(novoValor: saldo)
    } else {
        return .erro(mensagem: "Não há dinheiro suficiente")
    }
}

var saldo = 100
let resultado = saque(valor: 110)
switch resultado {
    case .sucesso(let novoValor): print("Seu novo saldo é de \(novoValor)")
    case .erro(let mensagem): print(mensagem)
}
```

*Associated values* são muito utilizados quando fazemos requisições para algum serviço externo.

## Iterando em casos

As vezes você deseja percorrer todos os casos em uma *enumeration*. Isso é fácil de fazer:

```swift
enum Mes: CaseIterable {
    case janeiro, fevereiro, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
}

for mes in Mes.allCases {
    print(mes)
}
```

`CaseIterable` é um protocolo que permite que `enum` seja tratado como coleção. Veremos mais sobre protocolos no próximo material.

## Curiosidade: Opcionais funcionam através do uso de Enums

Opcionais são `enums` com dois casos:
- `.none` significa que não possuem valor (ou seja, são `nil`).
- `.some` significa que existe um valor associado.

Veja o exemplo abaixo:

```swift
var nome: String?
nome = "Giovanna"

switch nome {
    case .none: print("A opcional não possui nenhum valor.")
    case .some(let valor): print("O valor da opcional é \(valor)")
}
```

Ir para a próxima página: [Protocolos](21-protocolos.md)