# Arrays

Agora vamos entrar em um outro tópico relacionado aos tipos de dados: as **coleções**.

Em primeiro lugar, temos os *arrays*, a coleção mais utilizada. São simples listas que possuem dados do mesmo tipo. 

Algo importante para lembrar é que o mesmo valor pode aparecer múltiplas vezes.

Arrays são úteis quando precisamos armazenar itens em uma ordem particular. 

## Criando um Array

Para criar um array vazio:

```swift
let numbers: [Int] = [] // precisamos especificar o tipo caso seja criado um array vazio
// ou
let numbers = Array<Int>()
```

Podemos criar um array já inserindo valores para ele. Nesse caso, o Swift consegue inferir o seu tipo automaticamente.

```swift
let numbers = [1, 4, 8, 10, 15]
```

## Acessando elementos

Cada elemento de um array possui um **index**, iniciando no zero. Portanto, o primeiro elemento de um array pode ser acessado por `numbers[0]`, que será retornado 1. 

Caso haja uma tentativa de acessar um elemento por um index inexistente, causará um erro chamado "index out of range" (index fora do intervalo). Como temos 5 elementos nesse array, o index vai de 0 até 4. O index 5 é inexistente, portanto tentar acessar `numbers[5]` causará erro.

Podemos usar algumas propriedades e métodos que a própria linguagem nos fornece, como por exemplo:

```swift
let numbers = [1, 4, 8, 10, 15]
print(numbers.isEmpty) // false
print(numbers.count) // 5
print(numbers.min()) // 1 (menor valor)
print(numbers.max()) // 15 (maior valor)
print(numbers.contains(8)) //true (o array possui o valor 8)
print(numbers.firstIndex(of: 8)) // 2 (o número 8 está no index 2)
```

## Adicionando, atualizando e removendo elementos

Para adicionar um elemento no final do array:

```swift
var numbers = [1, 4, 8, 10, 15]
numbers.append(3)
// [1, 4, 8, 10, 15, 3]
```

Note como `numbers` está declarado como variável agora, e não constante. Isso porque quando adicionamos um elemento estamos modificando o array, o que não é permitido com o uso de `let`.

Também podemos fazer dessa maneira:

```swift
var numbers = [1, 4, 8, 10, 15]
numbers += [3]
// [1, 4, 8, 10, 15, 3]
```

Para adicionar um elemento em determinada posição do array:

```swift
var numbers = [1, 4, 8, 10, 15]
numbers.insert(3, at: 1) // insere o valor 3 no index 1
// [1, 3, 4, 8, 10, 15]
```

Para atualizar um elemento:

```swift
var numbers = [1, 4, 8, 10, 15]
numbers[1] = 10
// [1, 10, 8, 10, 15]
```

Para remover um elemento:

- Se quiser remover o último elemento:

```swift
var numbers = [1, 4, 8, 10, 15]
var removedElement = numbers.removeLast() // retorna o elemento removido
```

- Se quiser remover o primeiro elemento:

```swift
var numbers = [1, 4, 8, 10, 15]
var removedElement = numbers.removeFirst()
```

- Se quiser remover um elemento em sua determinada posição:

```swift
var numbers = [1, 4, 8, 10, 15]
var removedElement = numbers.remove(at: 2) // elemento no index 2 será removido, ou seja, o valor 8
```

## Percorrendo um Array

Podemos percorrer um Array usando um loop. Veja abaixo o exemplo com `for`:

```swift
let numbers = [1, 4, 8, 10, 15]

for number in numbers {
    print(number)
}
```

Se quisermos obter o index de cada elemento, podemos usar um método chamado `enumerated()`. 

```swift
let numbers = [1, 4, 8, 10, 15]

for (index, number) in numbers.enumerated() {
    print(index, number)
}
```

