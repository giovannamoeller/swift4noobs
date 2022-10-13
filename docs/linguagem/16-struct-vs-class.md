# As diferenças entre struct e class

Primeiramente, precisamos entender que existem algumas funcionalidades extras que apenas as classes possuem, enquanto structures não:

- Classes podem herdar de outras classes, sendo assim, conseguem usar o conceito de herança para herdar atributos/métodos de uma classe pai. Structures não herdam nada: nem classes nem structs, só conformam a protocolos (assim como classes também podem conformar a protocolos);
- Possuem o conceito de "desinicializadores", utilizando o método deinit(). Dentro desse método, há um código que é executado quando uma instância de uma classe é destruída;
- As classes também podem ter uma ou mais referências para uma única instância, vamos ver esse conceito de referência a seguir.

**A principal diferença entre ambas é que classes são reference types (tipo de referência), enquanto structures são value types (tipo de valor).**

Para entender isso, veja o código abaixo:

```swift
struct Pessoa {
  var nome: String
  var sobrenome: String
  var idade: Int
}
var pessoa1 = Pessoa(nome: "John", sobrenome: "Doe", idade: 34)
var pessoa2 = pessoa1
pessoa1.nome = "Gabriel"
print(pessoa1.nome) // Gabriel
print(pessoa2.nome) // John
```

Perceba que igualamos `pessoa2` a `pessoa1` e então trocamos o valor da propriedade `nome` em `pessoa1`. Essa mudança aconteceu **apenas** em `pessoa1`, e não em `pessoa2`.

Agora, veja esse exemplo:

```swift
class Pessoa {
  var nome: String
  var sobrenome: String
  var idade: Int

  init(nome: String, sobrenome: String, idade: Int) {
    self.nome = nome
    self.sobrenome = sobrenome
    self.idade = idade
  }
}
var pessoa1 = Pessoa(nome: "John", sobrenome: "Doe", age: 34)
var pessoa2 = pessoa1
pessoa1.nome = "Gabriel"
print(pessoa1.nome) // Gabriel
print(pessoa2.nome) // Gabriel
```

Veja só: agora, mesmo alterando apenas o nome da variável `pessoa1`, a mudança também refletiu na variável `pessoa2`, fazendo com que ambos tenham o nome "Gabriel".

Isso acontece pois classes são *reference type*, ou seja, são passadas como referência, como mencionado acima.

## Entendendo mais sobre tipo de referência (reference type)

Quando estamos inicializando um objeto, a RAM aloca um espaço de memória e endereço para ele. Em seguida, atribui seu endereço de memória ao objeto que criamos.

<img src="https://www.alura.com.br/artigos/assets/ios-swift-classes-struct-diferencas-usar/img1.png">

Ou seja, como os objetos são do tipo referência (já que estão sendo declarados por uma classe), eles estão apontando para o **mesmo endereço de memória**, portanto, são na verdade os mesmos objetos! Se mudarmos uma de suas propriedades/atributos, o outro objeto também será afetado, pois está apontando para o mesmo endereço.

<img src="https://www.alura.com.br/artigos/assets/ios-swift-classes-struct-diferencas-usar/img2.png">

## Entendendo mais sobre tipo de valor (value type)

Value type significa que, quando atribuímos um valor para outro, cada instância mantém uma **cópia exclusiva dos dados**. Se você alterar uma instância, a outra não será modificada. Esse é o mesmo comportamento de tipos primitivos, como Int, String, Double, entre outros!

## Mais diferenças entre classes e structures

### Construtores

Uma outra diferença importante é que usando uma `struct`, você não precisa usar um construtor para inicializar as variáveis, pois ele já está lá indiretamente, como vimos em materiais anteriores.

Quando usamos classe, é obrigatório um construtor para a inicialização das variáveis.

### Modificação de propriedades

Além disso, as structures são **imutáveis**, então, se quisermos alterar uma propriedade dessa struct dentro de uma função, precisamos adicionar a palavra reservada **mutating** antes do nome da função. Veja o exemplo abaixo:

```swift
struct Pessoa {
  var nome: String
  var sobrenome: String
  var idade: Int

  mutating func mudarNome(novoNome: String) {
    self.nome = novoNome
  }
}
```

Com classes, esse comportamento não acontece.

### Imutabilidade com o uso de constantes

A última diferença entre classes e structures é que, quando utilizamos uma struct, não podemos alterar as propriedades de uma instância se ela for declarada com uma constante (let). Veja o exemplo abaixo:

```swift
struct Pessoa {
  var nome: String
  // Outras propriedades e métodos...
}
let pessoa1 = Pessoa(nome: "John", sobrenome: "Doe", idade: 34)
pessoa1.nome = "Gabriel" // erro!
```

Isso não acontece com o uso de classes! Mesmo se declararmos a instância com uma constante, nós podemos ainda alterar suas propriedades!

```swift
class Pessoa {
  var nome: String
  // Outras propriedades e métodos...
}
let pessoa1 = Pessoa(nome: "John", sobrenome: "Doe", idade: 34)
pessoa1.nome = "Gabriel" // A atribuição ocorre sem problemas
```

Por que isso acontece apenas com struct? Pois como as classes são *reference types*, a imutabilidade por referência é não poder modificar o endereço de memória dessa referência, apenas. Mas como structs são do tipo valor, nada pode ser modificado com o uso de constantes.

## Quando usar classes e quando usar structures?

Segundo a própria documentação da Apple, o ideal é utilizar struct por padrão. As structures em Swift são poderosas e possuem muitos recursos. Além disso, é mais seguro quando há a passagem por valor, em vez de passagem por referência (já que nesse caso, todas as instâncias estão conectadas entre si).

O próprio SwiftUI, framework de construção de aplicativos iOS, usa struct por padrão em muitos casos.

Porém, há alguns casos em que o uso de classes é recomendado:

- Quando você precisar utilizar o conceito de herança, herdar propriedades/métodos de uma outra classe pai;
- Quando você precisar de interoperabilidade, ou seja, utilizar um código de Objective-C, já que nessa linguagem não existe struct;
- Quando precisamos controlar a identidade, já que as classes em Swift vêm com uma noção embutida de identidade porque são tipos de referência.