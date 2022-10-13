# O uso de Generics

Já sabemos que Swift é uma linguagem fortemente tipada, significando que quando declaramos uma variável, precisamos já declarar qual o tipo de dado que será atribuído a essa variável. E, uma vez atribuído um certo tipo de dado, este não poderá ser alterado. 

## Entendendo a motivação por trás do uso de Generics

Vamos começar, criando uma função que soma dois valores:

```swift
func soma(a: Int, b: Int) -> Int {
    return a + b
}
let resultado = soma(a: 2, b: 3) // 5
```

Perceba que os parâmetros da função também precisam ter o seu tipo declarado. Se não declararmos um tipo para esses dados, acontece um erro de compilação e nossa aplicação não será executada.

Isso torna o nosso código muito limitado, pois podemos apenas somar dois números inteiros com essa função. Mas, e se precisarmos somar dois valores do tipo *double*? Precisamos criar outra função pra isso?

Se quisermos somar outros dois valores, só que agora do tipo *float*, precisaremos criar uma terceira função? Perceba que temos um problema: várias funções com o **mesmo objetivo** (somar dois valores), porém a única diferença é o tipo dos dados. Isso viola o princípio de código limpo pois há muita repetição de código. É esse o problema que o tipo genérico resolve.

## Usando Generics

*Generic*, portanto, é uma funcionalidade da linguagem Swift que permite criar funções, tipos, protocolos, enumerations, entre outros, que não estão vinculados a nenhum tipo de dado específico, mas que podem ser usados com qualquer tipo que atenda a um determinado conjunto de requisitos.

Você provavelmente já até usou generics no seu código. Por exemplo, array é uma estrutura de dados genérica, que nos permite criar instâncias de qualquer tipo de dado, como Int, String, ou até mesmo um tipo de dado personalizado que a gente criou.

Agora, voltando ao problema da função de soma que vimos anteriormente, como podemos resolver utilizando um tipo genérico, que nos permite somar diferentes tipos de dados? Veja abaixo o código:

```swift
func soma<T: Numeric>(a: T, b: T) -> T {
  return a + b
}

soma(a: 2.5, b: 3.0) // 5.5
soma(a: 5, b: 4) // 11
```

Vamos entender o que está acontecendo neste código. Primeiramente, criamos um tipo genérico de dados chamado `T`. `T` na verdade é uma convenção utilizada para determinar tipos genéricos. A própria documentação do Swift, explicando sobre generics, também utiliza a letra T para definir esse tipo.

Veja que os parâmetros `a` e `b` são do tipo `T`, e o retorno da função também é do tipo `T`.

Agora não estamos mais presos a apenas um tipo de dado, como *Int*, *Double* ou *Float*. Perceba, também, que declaramos esse tipo logo após a palavra 'soma', abrindo com o sinal de <>. Também, declaramos que o tipo genérico T é, na verdade, um tipo `Numeric`.

Basicamente essa sintaxe é uma maneira de indicar qual tipo específico queremos limitar para o generics. Esse tipo `Numeric` **engloba** todos os números, como *Int*, *Double*, ou até mesmo *Float*.

Por isso que conseguimos passar qualquer valor agora para a função, independente de ser um inteiro ou um decimal. É exatamente esse o problema que o generic resolve: reutilizar o mesmo código para tipos diferentes. Agora, não precisamos mais declarar uma função para cada tipo de dado numérico, que gerava uma repetição de código desnecessária.

## Criando uma classe genérica

Podemos também criar uma classe genérica que pode mudar o tipo de dado que recebe. Veja o exemplo abaixo:

```swift
class Informacao<T> {
  var dado: T
  init (dado: T) {
    self.dado = dado
  }
  func retornaDado() -> T {
    return self.dado
  }
}

var numero = Informacao<Int>(dado: 6)
print(numero.retornaDado()) // 6, um valor do tipo Int

var string = Informacao<String>(dado: "Hello, World!")
print(string.retornaDado()) // Hello World, um valor do tipo String
```

Ir para a próxima página: [E agora, pra onde ir?](23-next-steps.md)