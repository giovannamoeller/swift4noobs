# Iterando sobre coleções com closures

No Swift, existem vários métodos funcionais que podem ser usados com coleções. Esses métodos nos auxiliam no desenvolvimento, uma vez que tornam algo muito mais fácil.

Por exemplo, para filtrar um array, você pode usar um método `filter()` que é específico pra isso. Você não precisa criar nenhuma lógica por baixo dos panos.

Essas funcionalidades estão muito ligadas ao conceito de **functional programming**, ou seja, programação funcional.

Vamos ver alguns métodos abaixo. Todos utilizam o conceito de `closure`, passando uma função como argumento.

## 1. ForEach

O método `forEach` realiza um loop entre os elementos de uma coleção e perfrorma alguma operação entre eles:

```swift
let valores = [1, 4, 8, 10, 15, 16]
valores.forEach { valor in
    print(valor)
}
```

Veja que a função `forEach` recebe uma `closure` como argumento, uma função que será executada para todo elemento de uma coleção.

E tudo o que você viu no material anterior é aplicado aqui. Veja o código abaixo, em que omitimos a lista de parâmetros:

```swift
let valores = [1, 4, 8, 10, 15, 16]
valores.forEach {
    print($0)
}
```

## 2. Filter

Esse método é responsável por filtrar certos elementos de uma coleção:

```swift
let valores = [1, 4, 8, 10, 15, 16]
let valoresMaiorQue10 = valores.filter { valor in
    return valor > 10
} // [15, 16]
```

Nesse caso, estamos filtrando os elementos maior que 10.

Porém, perceba que esse método não atua diretamente no array `valores`. Ele retorna um outro array e você pode atribuí-lo à uma nova variável.

## 3. First

Esse método pega apenas o primeiro elemento que satisfaz uma determinada condição. Então seguindo o mesmo exemplo acima:

```swift
let valores = [1, 4, 8, 10, 15, 16]
let primeiroValorMaiorQue10 = valores.first { valor in
    return valor > 10
} // 15
```

## 4. Map

O método `map` executa determinda função em cada elemento do array e retorna um novo array com essas modificações:

```swift
let valores = [1, 4, 8, 10, 15, 16]
let valoresDobrados = valores.map { valor in
    return valor * 2
}
print(valoresDobrados) // [2, 8, 16, 20, 30, 32]
```

Obs: perceba que em todos esses métodos estamos usando a sintaxe de *trailing closure*.

## 5. CompactMap

Antes de entendermos o `compactMap`, vamos ver mais um exemplo de `map` abaixo:

```swift
let strings = ["0", "10", "Giovanna", "40"]
let valores = strings.map { string in
    return Int(string)
}
print(valores) // [Optional(0), Optional(10), nil, Optional(40)]
```

Veja que estamos retornando um array de números inteiros a partir da conversão. Mas, não podemos garantir que toda string seja de fato um número. É impossível converter "Giovanna" para um inteiro, por isso há o retorno em forma de opcional. Inclusive, temos até um `nil` ali no meio.

O que o `compactMap` faz é retornar o array com valores certos, sem usar opcionais, ele já faz a verificação:

```swift
let strings = ["0", "10", "Giovanna", "40"]
let valores = strings.compactMap { string in
    return Int(string)
}
print(valores) // [0, 10, 40]
```

Existem diversos outros métodos que iteram sobre coleções com o uso de `closures`, isso é uma prática muito comum!





