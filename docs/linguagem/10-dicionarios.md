# Dicionários

Um dicionário é uma coleção não ordenada de pares, onde cada par compreende uma chave e um valor. 

No Javascript por exemplo, um dicionário seria na verdade um objeto.

Chaves são únicas. A mesma chave não pode aparecer duas vezes em um dicionário, porém chaves diferentes podem apontar para um mesmo valor.

Todas as chaves precisam ser do mesmo tipo, enquanto todos os valores precisam ser do mesmo tipo.

Dicionários são úteis quando você pode querer valores que são identificados por uma chave. 

## Criando dicionários

O Swift consegue inferir o tipo abaixo:

```swift
var pessoas = ["Anna": 21, "Brian": 23, "Stella": 24, "Marc": 20]
```

Porém, se quiser **declarar** o tipo explicitamente:

```swift
var pessoas: [String: Int] = ["Anna": 21, "Brian": 23, "Stella": 24, "Marc": 20]
```

Para criar um dicionário vazio, você precisa declarar o tipo explicitamente:

```swift
var pessoas: [String: Int] = [:]
```

Uma curiosidade: para melhorar a performance, você pode reservar uma capacidade para o seu dicionário, caso saiba a quantidade de dados que ele possuirá:

```swift
var pessoas: [String: Int] = [:]
pessoas.reserveCapacity(20)
```

## Acessando valores

Para acessar valores, você pode acessar diretamente por uma chave.

```swift
var pessoas: [String: Int] = ["Anna": 21, "Brian": 23, "Stella": 24, "Marc": 20]
print(pessoas["Anna"])
```

Por questões de segurança, o valor retornado será opcional, pois o Swift não é capaz de saber se a chave existe ou não.

Se você tentar acessar o valor de uma chave inexistente, o resultado será `nil`.

Dicionários, assim como arrays, conformam ao protocolo de coleções, portanto possuem alguns métodos e propriedades em comum. Veja os exemplos abaixo:

```swift
var pessoas: [String: Int] = ["Anna": 21, "Brian": 23, "Stella": 24, "Marc": 20]
print(pessoas.isEmpty) // false
print(pessoas.count) // 4
```

## Modificando dicionários

### Adicionando pares

Para adicionar uma nova chave/valor em um dicionário, podemos fazer de duas formas:

```swift
var pessoas: [String: Int] = ["Anna": 21, "Brian": 23, "Stella": 24, "Marc": 20]
pessoas["Giovanna"] = 21
pessoas.updateValue(19, forKey: "Lucas") // já que não existe uma chave "Lucas", será criada uma e o retorno é nil
```

### Atualizando pares

Para atualizar valores, podemos utilizar os mesmos dois métodos vistos acima:

```swift
var pessoas: [String: Int] = ["Anna": 21, "Brian": 23, "Stella": 24, "Marc": 20]
pessoas["Anna"] = 22
pessoas.updateValue(25, forKey: "Stella") // retorna o valor antigo, 24. 
```

### Removendo pares

Para remover uma chave/valor, podemos utilizar dois métodos:

```swift
var pessoas: [String: Int] = ["Anna": 21, "Brian": 23, "Stella": 24, "Marc": 20]
pessoas["Anna"] = nil
// ou
pessoas.removeValue(forKey: "Anna")
```

## Iterando através de dicionários

Assim como em arrays, podemos iterar sobre dicionários com um loop, o `for in`. Veja o exemplo abaixo:

```swift
for (nome, idade) in pessoas {
    print(nome, idade)
}
```

Ou, podemos iterar sobre as chaves, apenas:

```swift
for (nome) in pessoas.keys {
    print(nome)
}
```

Ou até mesmo apenas sobre os valores:

```swift
for (idade) in pessoas.values {
    print(idade)
}
```

Mas, também podemos usar o método da omissão com o underline (_), como vimos em tuplas:

```swift
for (nome, _) in pessoas {
    print(nome)
}
```