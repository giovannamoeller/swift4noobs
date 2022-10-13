# Arrays

Agora vamos entrar em um outro tópico relacionado aos tipos de dados: as **coleções**.

Em primeiro lugar, temos os *arrays*, a coleção mais utilizada. São simples listas que possuem dados do mesmo tipo. 

Algo importante para lembrar é que o mesmo valor pode aparecer múltiplas vezes.

Arrays são úteis quando precisamos armazenar itens em uma ordem particular. 

## Criando um Array

Para criar um array vazio:

```swift
let numeros: [Int] = [] // precisamos especificar o tipo caso seja criado um array vazio
// ou
let numeros = Array<Int>()
```

Podemos criar um array já inserindo valores para ele. Nesse caso, o Swift consegue inferir o seu tipo automaticamente.

```swift
let numeros = [1, 4, 8, 10, 15]
```

## Acessando elementos

Cada elemento de um array possui um **index**, iniciando no zero. Portanto, o primeiro elemento de um array pode ser acessado por `numeros[0]`, que será retornado 1. 

Caso haja uma tentativa de acessar um elemento por um index inexistente, causará um erro chamado "index out of range" (index fora do intervalo). Como temos 5 elementos nesse array, o index vai de 0 até 4. O index 5 é inexistente, portanto tentar acessar `numeros[5]` causará erro.

Podemos usar algumas propriedades e métodos que a própria linguagem nos fornece, como por exemplo:

```swift
let numeros = [1, 4, 8, 10, 15]
print(numeros.isEmpty) // false
print(numeros.count) // 5
print(numeros.min()) // 1 (menor valor)
print(numeros.max()) // 15 (maior valor)
print(numeros.contains(8)) //true (o array possui o valor 8)
print(numeros.firstIndex(of: 8)) // 2 (o número 8 está no index 2)
```

## Adicionando, atualizando e removendo elementos

Para adicionar um elemento no final do array:

```swift
var numeros = [1, 4, 8, 10, 15]
numeros.append(3)
// [1, 4, 8, 10, 15, 3]
```

Note como `numeros` está declarado como variável agora, e não constante. Isso porque quando adicionamos um elemento estamos modificando o array, o que não é permitido com o uso de `let`.

Também podemos fazer dessa maneira:

```swift
var numeros = [1, 4, 8, 10, 15]
numeros += [3]
// [1, 4, 8, 10, 15, 3]
```

Para adicionar um elemento em determinada posição do array:

```swift
var numeros = [1, 4, 8, 10, 15]
numeros.insert(3, at: 1) // insere o valor 3 no index 1
// [1, 3, 4, 8, 10, 15]
```

Para atualizar um elemento:

```swift
var numeros = [1, 4, 8, 10, 15]
numeros[1] = 10
// [1, 10, 8, 10, 15]
```

Para remover um elemento:

- Se quiser remover o último elemento:

```swift
var numeros = [1, 4, 8, 10, 15]
var elementoRemovido = numeros.removeLast() // retorna o elemento removido
```

- Se quiser remover o primeiro elemento:

```swift
var numeros = [1, 4, 8, 10, 15]
var elementoRemovido = numeros.removeFirst()
```

- Se quiser remover um elemento em sua determinada posição:

```swift
var numeros = [1, 4, 8, 10, 15]
var elementoRemovido = numeros.remove(at: 2) // elemento no index 2 será removido, ou seja, o valor 8
```

## Percorrendo um Array

Podemos percorrer um Array usando um loop. Veja abaixo o exemplo com `for`:

```swift
let numeros = [1, 4, 8, 10, 15]

for numero in numeros {
    print(numero)
}
```

Se quisermos obter o index de cada elemento, podemos usar um método chamado `enumerated()`. 

```swift
let numeros = [1, 4, 8, 10, 15]

for (index, numero) in numeros.enumerated() {
    print(index, numero)
}
```

Ir para a próxima página: [Sets](docs/linguagem/09-sets.md)