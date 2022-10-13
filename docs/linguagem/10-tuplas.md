# Tuplas

Tuplas são coleções de dados que representa dados compostos por mais de um valor de qualquer tipo. 

Você pode ter quantos valores em sua tupla desejar. Por exemplo, você pode definir um par de coordenadas onde cada valor de eixo é um número inteiro, desse modo:

```swift
let coordenadas: (Int, Int) = (2, 3)
```

Para acessar esses elementos:

```swift
let coordenadas: (Int, Int) = (2, 3)
print(coordenadas.0) // 2
print(coordenadas.1) // 3
```

Se preferir, podemos dar nomes à esses valores:

```swift
let coordenadas = (x: 2, y: 3)
print(coordenadas.x) // 2
print(coordenadas.y) // 3
```

E para declarar explicitamente o tipo de dado acima, precisa ser dessa forma:

```swift
let coordenadas: (x: Int, y: Int) = (x: 2, y: 3)
print(coordenadas.x) // 2
print(coordenadas.y) // 3
```

Lembra quando vimos sobre `typealias`? Será um ótimo uso para o caso acima:

```swift
typealias Coordenadas = (x: Int, y: Int)
let coordenadas: Coordenadas = (x: 2, y: 3)
```

Como mencionado anteriormente, os valores não precisam ser do mesmo tipo, exemplo:

```swift
let pessoa: (nome: String, idade: Int) = (nome: "Giovanna", idade: 21)
```

Podemos usar uma forma de desestruturação para obter os valores:

```swift
let pessoa: (nome: String, idade: Int) = (nome: "Giovanna", idade: 21)
let (nome, idade) = pessoa
print(nome)
print(idade)
```

Caso seja necessário apenas a variável `idade`, podemos omitir a variável `nome` com o uso de underline (_):

```swift
let pessoa: (nome: String, idade: Int) = (nome: "Giovanna", idade: 21)
let (_, idade) = pessoa
print(idade)
```

Ir para a próxima página: [Dicionários](docs/linguagem/11-dicionarios.md)