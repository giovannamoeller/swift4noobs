# Tuplas

Tuplas são coleções de dados que representa dados compostos por mais de um valor de qualquer tipo. 

Você pode ter quantos valores em sua tupla desejar. Por exemplo, você pode definir um par de coordenadas onde cada valor de eixo é um número inteiro, desse modo:

```swift
let coordinates: (Int, Int) = (2, 3)
```

Para acessar esses elementos:

```swift
let coordinates: (Int, Int) = (2, 3)
print(coordinates.0) // 2
print(coordinates.1) // 3
```

Se preferir, podemos dar nomes à esses valores:

```swift
let coordinates = (x: 2, y: 3)
print(coordinates.x) // 2
print(coordinates.y) // 3
```

E para declarar explicitamente o tipo de dado acima, precisa ser dessa forma:

```swift
let coordinates: (x: Int, y: Int) = (x: 2, y: 3)
print(coordinates.x) // 2
print(coordinates.y) // 3
```

Lembra quando vimos sobre `typealias`? Será um ótimo uso para o caso acima:

```swift
typealias Coordinates = (x: Int, y: Int)
let coordinates: Coordinates = (x: 2, y: 3)
```

Como mencionado anteriormente, os valores não precisam ser do mesmo tipo, exemplo:

```swift
let person: (name: String, age: Int) = (name: "Giovanna", age: 21)
```

Podemos usar uma forma de desestruturação para obter os valores:

```swift
let person: (name: String, age: Int) = (name: "Giovanna", age: 21)
let (name, age) = person
print(name)
print(age)
```

Caso seja necessário apenas a variável `age`, podemos omitir a variável `name` com o uso de underline (_):

```swift
let person: (name: String, age: Int) = (name: "Giovanna", age: 21)
let (_, age) = person
print(age)
```

