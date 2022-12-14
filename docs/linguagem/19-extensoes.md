# Extensões

Extensão é uma funcionalidade extremamente poderosa da linguagem Swift em que você pode estender determinado tipo para que haja mais propriedades e métodos customizados sem modificar a definição original.

As vezes também queremos adicionar funcionalidades a tipos existentes mas não temos acesso ao código fonte. Mais uma razão para usarmos `extension`.

Veja o código abaixo, em que criamos uma extensão do tipo primitivo da linguagem Swift, `Int`:

```swift
extension Int {
    func soma(com numero: Self) -> Self {
        return self + numero
    }
}
```

Vamos entender melhor o que está acontecendo. Mas, veja agora um explo de aplicação desse método:

```swift
extension Int {
    func soma(com numero: Self) -> Self {
        return self + numero
    }
}

let value = 10
let soma = value.soma(com: 40)
print(soma) // 50
```

Criamos um novo método dentro do tipo `Int`. Esse método recebe um parâmetro que possui um tipo de `Self`. Note que o `Self` está escrito com 'S' maiúsculo na declaração da função e não minúsculo.

A diferença é que o `Self` faz referência ao próprio tipo em questão, enquanto o `self` faz referência a própria instância de determinado tipo.

Portanto, nessa função, `Self` está se referindo a `Int`, significando que `numero` é do tipo `Int` e o retorno dessa função também é do tipo `Int`. Enquanto o `self` está se referindo ao valor, à instância dessa `struct`.

Como a variável `value` é do tipo `Int`, então quer dizer que podemos acessar diferentes propriedades e métodos do `Int`. Agora, o método `soma` faz parte desse tipo, pois adicionamos via uma `extension`.

Extensões são muito utilizadas para melhor organização do código e separação de responsabilidades.

Podemos estender `struct`, `class`, `protocol` e `enum`.
Vamos ver sobre protocolos e enumerations a seguir.

Ir para a próxima página: [Enumerations](20-enumeracoes.md)
