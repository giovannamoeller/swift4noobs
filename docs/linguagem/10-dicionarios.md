# Dicionários

Um dicionário é uma coleção não ordenada de pares, onde cada par compreende uma chave e um valor. 

No Javascript por exemplo, um dicionário seria na verdade um objeto.

Chaves são únicas. A mesma chave não pode aparecer duas vezes em um dicionário, porém chaves diferentes podem apontar para um mesmo valor.

Todas as chaves precisam ser do mesmo tipo, enquanto todos os valores precisam ser do mesmo tipo.

Dicionários são úteis quando você pode querer valores que são identificados por uma chave. 

## Criando dicionários

O Swift consegue inferir o tipo abaixo:

```swift
var namesAndAges = ["Anna": 21, "Brian": 23, "Stella": 24, "Marc": 20]
```

Porém, se quiser **declarar** o tipo explicitamente:

```swift
var namesAndAges: [String: Int] = ["Anna": 21, "Brian": 23, "Stella": 24, "Marc": 20]
```

Para criar um dicionário vazio, você precisa declarar o tipo explicitamente:

```swift
var namesAndAges: [String: Int] = [:]
```

Uma curiosidade: para melhorar a performance, você pode reservar uma capacidade para o seu dicionário, caso saiba a quantidade de dados que ele possuirá:

```swift
var namesAndAges: [String: Int] = [:]
namesAndAges.reserveCapacity(20)
```

## Acessando valores

Para acessar valores, você pode acessar diretamente por uma chave.

```swift
var namesAndAges: [String: Int] = ["Anna": 21, "Brian": 23, "Stella": 24, "Marc": 20]
print(namesAndAges["Anna"])
```

Por questões de segurança, o valor retornado será opcional, pois o Swift não é capaz de saber se a chave existe ou não.

Se você tentar acessar o valor de uma chave inexistente, o resultado será `nil`.

Dicionários, assim como arrays, conformam ao protocolo de coleções, portanto possuem alguns métodos e propriedades em comum. Veja os exemplos abaixo:

```swift
var namesAndAges: [String: Int] = ["Anna": 21, "Brian": 23, "Stella": 24, "Marc": 20]
print(namesAndAges.isEmpty) // false
print(namesAndAges.count) // 4
```

## Modificando dicionários

### Adicionando pares

Para adicionar uma nova chave/valor em um dicionário, podemos fazer de duas formas:

```swift
var namesAndAges: [String: Int] = ["Anna": 21, "Brian": 23, "Stella": 24, "Marc": 20]
namesAndAges["Giovanna"] = 21
namesAndAges.updateValue(19, forKey: "Lucas") // já que não existe uma chave "Lucas", será criada uma e o retorno é nil
```

### Atualizando pares

Para atualizar valores, podemos utilizar os mesmos dois métodos vistos acima:

```swift
var namesAndAges: [String: Int] = ["Anna": 21, "Brian": 23, "Stella": 24, "Marc": 20]
namesAndAges["Anna"] = 22
namesAndAges.updateValue(25, forKey: "Stella") // retorna o valor antigo, 24. 
```

### Removendo pares

Para remover uma chave/valor, podemos utilizar dois métodos:

```swift
var namesAndAges: [String: Int] = ["Anna": 21, "Brian": 23, "Stella": 24, "Marc": 20]
namesAndAges["Anna"] = nil
// ou
namesAndAges.removeValue(forKey: "Anna")
```

## Iterando através de dicionários

Assim como em arrays, podemos iterar sobre dicionários com um loop, o `for in`. Veja o exemplo abaixo:

```swift
for (name, age) in namesAndAges {
    print(name, age)
}
```

Ou, podemos iterar sobre as chaves, apenas:

```swift
for (name) in namesAndAges.keys {
    print(name)
}
```

Ou até mesmo apenas sobre os valores:

```swift
for (age) in namesAndAges.values {
    print(age)
}
```

Mas, também podemos usar o método da omissão com o underline (_), como vimos em tuplas:

```swift
for (name, _) in namesAndAges {
    print(name)
}
```